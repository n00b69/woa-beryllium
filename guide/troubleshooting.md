<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Running Windows on the Xiaomi Pocophone F1

## Troubleshooting Issues
> Below you will find a list of common problems and their solutions

## LTE and other network services in Android no longer work
> Sometimes Windows may wipe your modem partitions, resulting in the loss of LTE in Android. To fix this, you'll need to restore your modem using the backups that you hopefully made [while partitioning your device](1-partition.md#backing-up-important-files). If you did not do this step, there is likely no way to recover.
- Boot into any recovery other than the stock recovery (ADB commands do not work there)
- Open CMD in the **platform-tools** folder.
- Restore the four partitions that you backed up using the below commands. Replace `path\to` with the actual path of the images.
```cmd
adb push path\to\fsc.bin /cache/ & adb shell dd if=/cache/fsc.bin of=/dev/block/by-name/fsc
```

```cmd
adb push path\to\fsg.bin /cache/ & adb shell dd if=/cache/fsg.bin of=/dev/block/by-name/fsg
```

```cmd
adb push path\to\modemst1.bin /cache/ & adb shell dd if=/cache/modemst1.bin of=/dev/block/by-name/modemst1
```

```cmd
adb push path\to\modemst2.bin /cache/ & adb shell dd if=/cache/modemst2.bin of=/dev/block/by-name/modemst2
```
- Reboot your device and check if LTE works.
> [!Note]
> If it still does not work, you will have to do some additional steps;
- Download the [stock rom for your device](https://xmfirmwareupdater.com/miui/beryllium/)
- Open it, look for a file called **modem.img** and extract it.
- Boot into fastboot mode (`adb reboot bootloader`).
- Flash this **modem.img** with the below command, replacing `path\to\modem.img` with the actual path of the image
```cmd
fastboot flash modem path\to\modem.img
```

##### Finished!

## LTE in Windows does not work
> [!Note]
> You may have to follow the steps above to restore your modem first
- In Android, find your APN settings. It should be located in `Connections` > `Mobile Networks` > `Access Point Names`.
- Write the information of your current APN settings down, then boot into Windows.
- In `Cellular Settings`, click on `Mobile operator settings` > `APN settings` and add the APN settings you wrote down earlier.
- Enable **Cellular**. It may say `No Internet Access`, but it should still work. 

##### Finished!

## Device is not recognized in fastboot or recovery
> This likely means you don't have (proper) USB drivers installed
- Download [QUD.zip](https://github.com/n00b69/woa-betalm/releases/download/Qfil/QUD.zip) here and extract it.
- Open Device Manager and find an unknown device or device with errors that may be called **Android**, **ADB Interface**, or **QUSB_BULK**.
- Right click this devjce, select "Update Drivers" > "Browse files", then select the **QUD folder** you extracted before.

##### Finished!

## Cannot mount Windows in Android
If mounting Windows produces an empty folder, you either don't have Windows installed, or your rom does not have mount support.

##### Finished!

## Cannot write to Windows in Android
> This is caused by shutting down Windows instead of restarting it.
- To solve this, boot to Windows and then press "restart", then as the screen shuts off boot to TWRP and from there load up Android.
- Or, disable hibernation in Windows using [this](https://github.com/n00b69/woa-beryllium/releases/tag/1.0) script 
> Alternatively, if you have already set up the Switch to Android app, simply use this to switch to Android.

##### Finished!

## USB does not work
Enable USB host mode using the [additional materials guide](materials.md).

##### Finished!

## Error: 3 The system cannot find the path specified.
This error usually means that you are trying to install Windows on a disk that already has Windows installed. To solve this issue, format the disk in Windows Explorer and try again.

##### Finished!

## 0xc000021a BSOD
This usually means that winlogon.exe has failed, and you may need to reapply the Windows image.

##### Finished!

## The computer restarted unexpectedly or encountered an unexpected error
If you stumble upon this error, you will need to [reinstall Windows](reinstall.md).

##### Finished!

## INACCESSIBLE_BOOT_DEVICE BSOD
This Blue Screen of Death likely means some broken driver installation. To fix this, [reinstall Windows](reinstall.md).

##### Finished!














