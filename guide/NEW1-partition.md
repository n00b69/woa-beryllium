<img align="right" src="https://github.com/n00b69/woaberyllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">


# Running Windows on the Xiaomi Pocophone F1

## Installation

## Partitioning your device

### Prerequisites
- A brain (most important of all)

- [TWRP](https://github.com/n00b69/woaberyllium/releases/download/Recoveries/twrp.img)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)


### Notes
> [!WARNING]  
> All your data will be erased! Back up now if needed.
> 
> Do not run the same command twice unless specified.
>  
> Do not run all commands at once, execute them in order!
>
> YOU CAN BREAK YOUR DEVICE WITH THE COMMANDS BELOW IF YOU DO THEM WRONG!!!
>
> DO NOT REBOOT YOUR PHONE! If you think you made a mistake, ask for help in the [Telegram chat](https://t.me/WinOnF1).


> [!IMPORTANT]
> Make sure you use the provided recovery image in this guide. The instructions will not work on other recoveries.

##### Flash the modded recovery
> Open a CMD window inside the platform-tools folder, then (while your phone is in fastboot mode) run
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

##### Run the partitioning script
> Replace $ with the amount of storage you want Windows to have (do not add GB, just write the number)
> 
> If it asks you to run it once again, do so
```cmd
adb shell partition $
```

#### Check if Android still starts
Just restart the phone, and see if Android still works


## [Next step: Installing Windows](/guide/2-install.md)






