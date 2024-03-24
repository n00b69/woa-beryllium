<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Running Windows on the Xiaomi Pocophone F1

## Installing Windows

### Prerequisites

- [Windows on ARM image](https://worproject.com/esd)
  
- [Drivers](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)
  
- [Msc script](https://github.com/n00b69/woa-beryllium/releases/download/Files/msc.sh)

- [Touch fix script](https://github.com/n00b69/woa-beryllium/releases/download/Files/touchfix.bat)

- [Parted](https://github.com/n00b69/woa-beryllium/releases/download/Files/parted)
  
- [TWRP](https://github.com/n00b69/woa-beryllium/releases/download/Recoveries/twrp.img) (should already be installed)

#### Boot to TWRP
> If rebooting on the last page has replaced your recovery back to stock, flash it again in fastboot with:
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

#### Running the msc script
> Put msc.sh in the platform-tools folder, then run:
```cmd
adb push msc.sh / && adb shell sh msc.sh
```

### Diskpart
>  [!WARNING]
> DO NOT ERASE ANY PARTITION WHILE IN DISKPART!!!! THIS WILL ERASE ALL OF YOUR UFS!!!! THIS MEANS THAT YOUR DEVICE WILL BE PERMANENTLY BRICKED WITH NO SOLUTION! (except for taking the device to Xiaomi or flashing it with EDL, both of which will likely cost money)

```cmd
diskpart
```

#### Finding your phone
> This will list all connected disks
```cmd
lis dis
```

#### Selecting your phone
> Replace $ with the actual number of your phone (it should be the last one)
```cmd
sel dis $
```

#### Listing your phone's partitions
> This will list your device's partitions
```cmd
lis par
```

#### Selecting the Windows partition
> Replace $ with the partition number of Windows (should be 23)
```cmd
sel par $
```

#### Formatting Windows drive
```cmd
format quick fs=ntfs label="WINF1"
```

#### Add letter to Windows
```cmd
assign letter x
```

#### Selecting the ESP partition
> Replace $ with the partition number of ESP (should be 22)
```cmd
sel par $
```

#### Formatting ESP drive
```cmd
format quick fs=fat32 label="ESPF1"
```

#### Add letter to ESP
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

#### Running parted
```cmd
adb push parted /cache/ && adb shell "chmod 755 /cache/parted" && adb shell /cache/parted /dev/block/sda
```

#### Making ESP bootable
> Use `print` to see all partitions. Replace "$" with your ESP partition number, which should be 22
```cmd
set $ esp on
```

#### Exit parted
```sh
quit
```

#### Installing Drivers
> Extract the drivers folder from the archive, then run the following command, replacing`<path\to\drivers>` with the actual path of the drivers folder
```cmd
dism /image:X:\ /add-driver /driver:<path\to\drivers> /recurse
```

#### Fixing touch
> Run the `touchfix.bat` file as an administrator, or touch will not work when you boot into Windows
  
#### Create Windows bootloader files
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Enabling test signing
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Disabling recovery
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" recoveryenabled no
```

#### Disabling integrity checks
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" nointegritychecks on
```

### Unassign disk letters
> So that they don't stay there after disconnecting the device
```cmd
diskpart
```

#### Select the Windows volume of the phone
> Use `list volume` to find it, replace "$" with the actual number of **WINF1**
```diskpart
select volume $
```

#### Unassign the letter X
```diskpart
remove letter x
```

#### Select the ESP volume of the phone
> Use `list volume` to find it, replace "$" with the actual number of **ESPF1**
```diskpart
select volume $
```

#### Unassign the letter Y
```diskpart
remove letter y
```

#### Exit diskpart
```diskpart
exit
```

#### Checking panel type
> This should output either `dsi_ebbg_fhd_ft8719_video_display` or `dsi_tianma_fhd_nt36672a_video_display`
```cmd
adb shell dmesg | grep dsi_display_bind
```
Remember your panel type (Tianma or EBBG), you will need this later

### Reboot to Android
> To set up dualboot

## [Last step: Setting up dualboot](/guide/dualboot.md)

















