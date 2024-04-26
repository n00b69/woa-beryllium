<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Running Windows on the Xiaomi Pocophone F1

## Partitioning your device

### Prerequisites
- A brain (most important of all)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Modded OFOX recovery](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Notes
> [!WARNING]  
> Do not run the same command twice unless specified.
> 
> DO NOT REBOOT YOUR PHONE! If you think you made a mistake, ask for help in the [Telegram chat](https://t.me/WinOnF1).
> 
> Do not run all commands at once, execute them in order!

#### Flash the modded OFOX recovery
> Open a CMD window inside the platform-tools folder, then (while your phone is in fastboot mode) run
```cmd
fastboot flash recovery path\to\ofox-beryllium.img reboot recovery
```

#### Backing up important files
Use OFOX now to back up your Modem and EFS partition (as well as anything else if you have important data). Move this backup to a safe place (e.g your PC) as the next steps will wipe your data.

> [!Warning]
> All of your data will be erased. This is your last chance to back up.
> 
> **IF YOU PROCEED WITHOUT BACKING UP MODEM AND EFS, YOU ARE ON YOUR OWN IF YOU MESS UP**

### Run the partitioning script
> Replace **$** with the amount of storage you want Windows to have (do not add GB, just write the number)
> 
> If it asks you to run it once again, do so
```cmd
adb shell partition $
```

#### Checking your panel type
> Remember the output (Tianma or EBBG), you will need this later in the guide
```cmd
adb shell panel
```

### Check if Android still starts
- Just restart the phone, and see if Android still works

## [Next step: Installing Windows](/guide/2-install.md)





















