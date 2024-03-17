<img align="right" src="https://github.com/n00b69/woaberyllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">


# Running Windows on the Xiaomi Pocophone F1

## Installing Windows

### Prerequisites

- [Windows on ARM image](https://worproject.com/esd)
  
- [UEFI image](https://github.com/n00b69/woaberyllium/releases/tag/UEFI)
  
- [Drivers](https://github.com/n00b69/woaberyllium/releases/download/Drivers/2210.drivers+usbFixup+AudioFixup+rpcd.zip)

- [Touch fix script](https://github.com/n00b69/woaberyllium/releases/download/Files/touchfix.bat)
  
- [TWRP](https://github.com/n00b69/woaberyllium/releases/download/Recoveries/twrp.img) (should already be installed)

#### Boot to TWRP
> If rebooting on the last page has replaced your recovery back to stock, flash it again in fastboot with:
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

#### Running the msc script
> If it asks you to run it again, do so
```cmd
adb shell msc
```

### Diskpart
>  [!WARNING]
> DO NOT CLEAN OR ERASE ANY PARTITION WHILE IN DISKPART!!!! THIS WILL ERASE ALL OF YOUR UFS!!!! THIS MEANS THAT YOUR DEVICE WILL BE PERMANENTLY BRICKED WITH NO SOLUTION! (except for taking the device to Xiaomi or flashing it with EDL, both of which will likely cost money)

#### Opening diskpart
> This might open a new window, if it does, run the next commands in said window
```cmd
diskpart
```

#### Find the Windows and ESP volumes
> This will print a list of all current volumes connected to your PC
```cmd
list volume
```

#### Selecting the Windows volume
> Replace $ with the actual number of WINBERYLLIUM
```cmd
select volume $
```

#### Assign letter to WINMH2LM
> Replace $ with the actual number of WINBERYLLIUM
```cmd
assign letter x
```

#### Selecting the ESP volume
> Replace $ with the actual number of ESPBERYLLIUM
```cmd
select volume $
```

#### Assign letter to ESPBERYLLIUM
> Replace $ with the actual number of WINMBERYLLIUM
```cmd
assign letter y
```

#### Exit diskpart
```cmd
exit
```

### Installing Windows
> Replace `<path\to\install.esd>` with the actual path of install.esd (it may also be named install.wim)

```cmd
dism /apply-image /ImageFile:<path\to\install.esd> /index:6 /ApplyDir:X:\
```

> If you get `Error 87`, check the index of your image with `dism /get-imageinfo /ImageFile:<path\to\install.esd>`, then replace `index:6` with the actual index number of Windows 11 Pro in your image

#### Installing drivers
> Unpack the driver archive, then open the `OfflineUpdater.cmd` file

> Enter the drive letter of `Windows`, which should be X, then press enter

#### Fixing touch
> Run the `touchfix.bat` file as an administrator, or touch will not work when you boot into Windows
  
#### Create Windows bootloader files
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Configuring bootloader files
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

### Unassign disk letters
> So that they don't stay there after disconnecting the device
```cmd
diskpart
```

#### Select the Windows volume of the phone
> Use `list volume` to find it, it's the one named "Windows"
```diskpart
select volume <number>
```

#### Unassign the letter X
```diskpart
remove letter x
```

#### Select the ESP volume of the phone
> Use `list volume` to find it, it's the one named "ESP"
```diskpart
select volume <number>
```

#### Unassign the letter Y
```diskpart
remove letter y
```

#### Exit diskpart
```diskpart
exit
```

### Backing up boot images

#### Reboot your recovery
> To remove the msc script
- Reboot to recovery through TWRP, or run
```cmd
adb reboot recovery
```

#### Push the UEFI to your phone
> Drag and drop the UEFI to your phone

#### Back up your Android boot image
Use the TWRP backup feature to backup your Android boot image. Name this backup "Android"

#### Flash the UEFI
Use the TWRP install feature to flash the UEFI image to your boot partition. Select "install image", then locate the image.

#### Back up your Windows boot image
Use the TWRP backup feature to backup your Windows boot image. Name this backup "Windows"

#### Boot into Windows
After having flashed the UEFI image, reboot your phone.

### Setting up Windows
Your device will now set up Windows. This will take some time. It will eventually reboot, and after that the initial setup (oobe) should launch.

> [!Note]
> To skip the Microsoft Account login, use "g" for the email and password. Windows will then let you make a local account

## [Last step: Setting up dualboot](/guide/dualboot.md)
















