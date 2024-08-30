<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Ponowna instalacja Windows

### Wymagania
- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Zmodyfikowane recovery OFOX](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Uruchom recovery OFOX
> Jeśli Twój recovery został zastąpiony recovery domyślnym, sflashuj go ponownie za pomocą
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

#### Formatowanie Windows
```cmd
adb shell format
```

## [Następny Krok: Ponowna instalacja Windows](3-install.md)











