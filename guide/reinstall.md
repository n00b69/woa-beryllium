<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Running Windows on the Xiaomi Pocophone F1

## Reinstalling Windows

### Prerequisites

- [Windows on ARM image](https://worproject.com/esd)

- [Drivers](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)

- [Touch fix script](https://github.com/n00b69/woa-beryllium/releases/download/Files/touchfix.bat)
  
- [UEFI image](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

### Boot to the UEFI
> Replace **<path\to\beryllium-uefi.img>** with the actual path of the UEFI image
```cmd
fastboot boot <path\to\beryllium-uefi.img>
```

#### Enabling mass storage mode
> Once booted into the UEFI, use the volume buttons to navigate the menu and the power button to confirm
- Select UEFI Boot Menu.
- Select USB Attached SCSI (UAS) Storage.
- Select Boot.

### Diskpart
```cmd
diskpart
```

### List device volumes
> To print a list of all the connected volumes, run
```cmd
list volume
```

#### Select Windows volume
> Replace $ with the actual number of **WINF1**
```cmd
select volume $
```

#### Add letter to Windows
```cmd
assign letter x
```

#### Exit diskpart
```cmd
exit
```

#### Formatting Windows
> Go to Windows Exlorer > This PC and select **WINF1**. Right click and format as NTFS

### Installing Windows
> Replace `<path\to\install.esd>` with the actual path of install.esd (it may also be named install.wim)

```cmd
dism /apply-image /ImageFile:<path\to\install.esd> /index:6 /ApplyDir:X:\
```

> If you get `Error 87`, check the index of your image with `dism /get-imageinfo /ImageFile:<path\to\install.esd>`, then replace `index:6` with the actual index number of Windows 11 Pro in your image

### Installing Drivers
> Unpack the driver archive, then open the `OfflineUpdater.cmd` file

> Enter the drive letter of **WINF1**, which should be X, then press enter

#### Fixing touch
> Run the `touchfix.bat` file as an administrator, or touch will not work when you boot into Windows

### Boot into Windows
Reboot your phone. If you end up in Android instesd of Windows, flash the UEFI again using WOA Helper.

#### Setting up Windows
> Your device will now set up Windows. This will take some time. It will eventually reboot, and after that the initial setup (oobe) should launch.

> [!Note]
> To skip the Microsoft Account login, use "g" for the email and password. Windows will then let you make a local account

## Finished!
















