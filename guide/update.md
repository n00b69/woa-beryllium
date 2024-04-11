<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Running Windows on the Xiaomi Pocophone F1

## Updating drivers

### Prerequisites
- [Drivers](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)

### Boot into Windows
> Flash the UEFI image in fastboot or use the WOA Helper app

### Installing Drivers
> Unpack the driver archive on beryllium, then open the `OnlineUpdater.cmd` file

> Follow any instructiona provided on the screen

## Finished!

## Method 2: PC required
> This method is inferior to method 1, only use it if method 1 failed.

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Drivers](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)
  
- [UEFI image](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

### Boot to the UEFI
> Replace **<path\to\beryllium-uefi.img>** with the actual path of the UEFI image
```cmd
fastboot boot <path\to\beryllium-uefi.img>
```

#### Enabling mass storage mode
> Once booted into the UEFI, use the volume buttons to navigate the menu and the power button to confirm
- Select **UEFI Boot Menu**.
- Select **USB Attached SCSI (UAS) Storage**.
- Press the **power** button twice to confirm.

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

#### Boot back into Windows
> Reboot your device to boot back into Windows. If this boots you to Android, reflash the UEFI image through fastboot or by using the WOA Helper app


## Finished!



















