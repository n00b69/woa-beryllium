<img align="right" src="https://github.com/n00b69/woaberyllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Running Windows on the Xiaomi Pocophone F1

## Reinstalling Windows
> This guide is used for when you wish to completely reinstall Windows, without having to repartition

### Prerequisites

- [Windows on ARM image](https://worproject.com/esd)
  
- [UEFI image](https://github.com/n00b69/woaberyllium/releases/tag/UEFI)
  
- [Drivers](https://github.com/n00b69/woaberyllium/releases/download/Drivers/2210.drivers+usbFixup+AudioFixup+rpcd.zip)
  
- [Msc script](https://github.com/n00b69/woaberyllium/releases/download/Files/msc.sh)

- [Touch fix script](https://github.com/n00b69/woaberyllium/releases/download/Files/touchfix.bat)
  
- [TWRP](https://github.com/n00b69/woaberyllium/releases/download/Recoveries/twrp.img) (should already be installed)

#### Boot to TWRP
> If Xiaomi has replaced your recovery back to stock, flash it again in fastboot with:
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

#### Running the msc script
> Put msc.sh in the platform-tools folder, then run:
```cmd
adb push msc.sh / && adb shell sh msc.sh
```

### Diskpart
```cmd
diskpart
```

#### List device volumes
> To print a list of all the connected volumes, run
```cmd
list volume
```

#### Select Windows volume
> Replace $ with the actual number of the Windows volume
```cmd
select volume $
```

#### Assign letter to Windows
```cmd
assign letter x
```

#### Select ESP volume
> Replace $ with the actual number of the ESP volume
```cmd
select volume $
```

#### Assign letter to ESP
```cmd
assign letter y
```

### Exit diskpart
```cmd
exit
```
#### Formatting Windows drive
> In Windows Explorer (under My PC) locate the X: Windows drive
>
> Right click and fast format it as NTFS

#### Formatting ESP drive
> In Windows Explorer (under My PC) locate the Y: ESP drive
> 
> Right click and fast format it as Fat32

### Installing Windows
> Replace `<path\to\install.esd>` with the actual path of install.esd (it may also be named install.wim)

```cmd
dism /apply-image /ImageFile:<path\to\install.esd> /index:6 /ApplyDir:X:\
```

> If you get `Error 87`, check the index of your image with `dism /get-imageinfo /ImageFile:<path\to\install.esd>`, then replace `index:6` with the actual index number of Windows 11 Pro in your image

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
> Use `lis vol` to find it, it's the one named "Windows"
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

### Boot into Windows
Reboot your phone to boot back into Windows. If you end up in Android, use the WoA Helper app to switch to Windows. Make sure the UEFI in your UEFI folder is up to date.

## Finished!
















