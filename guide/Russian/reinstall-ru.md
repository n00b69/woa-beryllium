<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Переустановка Windows

### Требования
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Modded OFOX recovery](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Прошейте OFOX recovery
> Если ваше recovery было заменено стоковым, прошейте его снова используя
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

#### Отформатировать раздел Windows
```cmd
adb shell format
```

## [Следующий шаг: Установка Windows](2-install-ru.md)







