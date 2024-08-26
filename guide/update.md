<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Running Windows on the Xiaomi Pocophone F1

## Updating drivers

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Drivers](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)
  
- [Modded OFOX recovery](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Boot into the modded recovery
> If your recovery has been replaced by the stock recovery, flash it again using
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

#### Enabling mass storage mode
> If it asks you to run it once again, do so
```cmd
adb shell msc
```

### Diskpart
```cmd
diskpart
```

#### Select Windows volume
> Use `list volume` to find it, replace `$` with the actual number of **WINF1**
```cmd
select volume $
```

#### Assign the letter X
```cmd
assign letter x
```

#### Exit diskpart
```cmd
exit
```

### Installing Drivers
> [!Note]
> This process will take +- 20 minutes. Do not worry, this is normal.

- Unpack the driver archive, then open the `OfflineUpdater.cmd` file (if an error shows up, run `OfflineUpdaterFix.cmd` instead)

> If it asks you to enter a letter, enter the drive letter of **WINF1** (which should be **X**), then press enter

#### Reboot your device
> Make sure to also change the UEFI image in Android, otherwise you may face a "blue screen of death" (BSoD) when booting Windows later.
```cmd
adb reboot
```

## Finished!















