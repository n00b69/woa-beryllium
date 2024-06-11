<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Running Windows on the Xiaomi Pocophone F1

## Reinstalling Windows

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Modded OFOX recovery](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Boot into OFOX
> If MIUI has replaced your recovery, boot to fastboot and run
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

#### Formatting the Windows partition
```cmd
adb shell format
```

## [Next step: Reinstalling Windows](2-install.md)











