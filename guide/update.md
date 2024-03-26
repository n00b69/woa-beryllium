<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Running Windows on the Xiaomi Pocophone F1

## Updating drivers

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Drivers](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)
  
- [Msc script](https://github.com/n00b69/woa-beryllium/releases/download/Files/msc.sh)

- [Touch fix script](https://github.com/n00b69/woa-beryllium/releases/download/Files/touchfix.bat)
  
- [TWRP](https://github.com/n00b69/woa-beryllium/releases/download/Recoveries/twrp.img) (should already be installed)

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
> Replace $ with the actual number of **WINF1**
```cmd
select volume $
```

#### Assign letter to WINF1
```cmd
assign letter x
```

### Exit diskpart
```cmd
exit
```

### Installing Drivers
> Unpack the driver archive, then open the `OfflineUpdater.cmd` file

> Enter the drive letter of **WINF1**, which should be X, then press enter

#### Fixing touch
> Run the `touchfix.bat` file as an administrator, or touch will not work when you boot into Windows

### Unassign disk letter
> So that it doesn't stay there after disconnecting the device
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

#### Exit diskpart
```diskpart
exit
```

#### Boot back into Windows
> Reboot your device to boot back into Windows. If this boots you to Android, reflash the UEFI image through fastboot or by using the WOA Helper app


## Finished!



















