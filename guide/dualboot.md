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
> [!NOTE]
> If you are unable to move files to the Windows folder, it means you shut down Windows instead of restarting it. To fix this issue, boot back to Windows and use restart, then as it restarts boot to fastboot and use it to return to Android

- Download and install the WOA Helper app, then open it and grant it root access.
- Download the UEFI image and place it inside the folder named `UEFI` in your internal storage. If this folder does not exist, create it.
- Return to the WOA Helper app and press the `Back up Android boot` button. Select both the `Windows` and `Android` options.
- Press the `Mount Windows` button to mount Windows to your internal storage at `/sdcard/Windows`
- Create a folder called `sta` in Windows and unpack the two files in the 'Switch to Android package` file here (the files should go to `/sdcard/Windows/sta`
- Return to the WOA Helper app and press `Quickboot to Windows`.

### Setup - Windows
- Navigate to C:\sta and create a shortcut of `sta.exe` to your desktop.

##### Booting to Android
  - Run the new shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access)

##### Booting to Windows
  - Press `Quickboot to Windows` inside the app, or use the newly created toggle in your quick settings panel
  
## Finished!








