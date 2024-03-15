<img align="right" src="https://github.com/n00b69/woaberyllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">


# Running Windows on the Xiaomi Pocophone F1

## Dualboot guide

> [!NOTE] 
> There are two methods, use whichever one suits your situation the most. Method 1 requires root, while method 2 does not.

### Prerequisites
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [UEFI image]() EDIT

- [WOA Helper app](https://github.com/n00b69/woaberyllium/releases/download/Dualboot/woahelper.apk)

- [Switch To Android package](https://github.com/n00b69/woaberyllium/releases/download/Dualboot/beryllium.zip)


## Setting up a seamless dualboot

This guide assumes you are rooted, if you aren't, please follow [this guide](root.md) first.

### Setup - Android
- Create a folder named "UEFI" on your internal storage and place the UEFI image here
- Download both the WOA Helper app as well as the StA Installer
- Install and open WOA Helper and allow any root access it wants
- Press the "BACKUP ANDROID BOOT" button, which will back up your boot image to /sdcard/boot.img (internal storage)
- Also press the "Mount/Unmount Windows" button to mount Windows to /sdcard/Windows
- Move/copy the StA Installer and boot.img to /sdcard/Windows
- Return to the WOA Helper app and press "Quickboot to Windows"

### Setup - Windows
- Navigate to C:\sta and create a shortcut of `sta.exe` to your desktop.

##### Booting to android
  - Run the new shortcut on your desktop as **ADMINISTRATOR**

##### Booting to windows
  - Run the app
  - Press "Quickboot to windows"
  
## Finished!








