<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Установка Windows

### Требования
- [Образ ARM Windows](https://worproject.com/esd)
  
- [Драйвера](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)
  
- [Modded OFOX recovery](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Прошейте OFOX recovery
> Если ваше recovery было заменено стоковым, прошейте его снова используя
```cmd
fastboot flash recovery path\to\ofox-beryllium.img reboot recovery
```

#### Включите режим mass storage
> Если он попросит вас запустить его ещё раз, сделайте это
```cmd
adb shell msc
```

### Diskpart
> [!WARNING]
> НЕ УДАЛЯЙТЕ, НЕ СОЗДАВАЙТЕ И НЕ ИЗМЕНЯЙТЕ КАКИМ-ЛИБО ИНЫМ ОБРАЗОМ РАЗДЕЛЫ, НАХОДЯСЬ В DISKPART!!! ЭТО МОЖЕТ ПРИВЕСТИ К УДАЛЕНИЮ UFS ИЛИ НЕВОЗМОЖНОСТИ ЗАГРУЗКИ В FASTBOOT!!! ЭТО ОЗНАЧАЕТ, ЧТО ВАШЕ УСТРОЙСТВО БУДЕТ ОКИРПИЧЕНО БЕЗ КАКОГО-ЛИБО РЕШЕНИЯ! (за исключением доставки устройства в Xiaomi или его перепрошивки с помощью EDL, и то, и другое, скорее всего, будет стоить денег)
```cmd
diskpart
```

#### Выберите раздел Windows телефона
> Используйте `list volume` чтобы найти его, замените `$` номером раздела **WINF1**
```diskpart
select volume $
```

#### Добавьте букву к разделу Windows
```cmd
assign letter X
```

#### Выберите раздел ESP телефна
> Используйте `list volume` чтобы найти его, замените `$` номером раздела **ESPF1**
```cmd
select volume $
```

#### Добавьте букву к ESP
```cmd
assign letter Y
```

#### Выйдите из diskpart
```cmd
exit
```

### Установка Windows
> Замените `путь\к\install.esd` актуальным путём к install.esd (файл также может называться install.wim)
```cmd
dism /apply-image /ImageFile:путь\к\install.esd /index:6 /ApplyDir:X:\
```

> Если вы получите `Error 87`, проверьте индекс вышего образа используя `dism /get-imageinfo /ImageFile:путь\к\install.esd`, затем замените `index:6` действтельным индексом **Windows 11 Pro** в вашем образе

### Установка драйверов
> Распакуйте пакет драйверов, затем откройте файл `OfflineUpdater.cmd` 

> Введите букву диска **WINF1** (должна быть **X**) затем нажмите Enter
  
#### Создайте файлы загрузчика Windows
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Включите тестовую подпись
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Отключите восстановление
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" recoveryenabled no
```

#### Отключите проверку целостности
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" nointegritychecks on
```

### Отвяжите буквы дисков
> Чтобы они не остались после отключения устройства
```cmd
diskpart
```

#### Выберите раздел Windows телефона
> Используйте `list volume` чтобы найти его, замените `$` номером раздела **WINF1**
```cmd
select volume $
```

#### Отвяжите букву X
```cmd
remove letter x
```

#### Выберите раздел ESP телефна
> Используйте `list volume` чтобы найти его, замените `$` номером раздела **ESPF1**
```cmd
select volume $
```

#### Отвяжите букву Y
```cmd
remove letter y
```

#### Выйдите из diskpart
```cmd
exit
```

### Reboot to fastboot
```cmd
adb reboot bootloader
```

#### Booting firstboot.img
> Download **firstboot-paneltype.img** for your device's panel and replace `путь\к\firstboot-paneltype.img` with the actual path to the image
>
> Use `adb shell panel` if you forgot what panel you have
```cmd
fastboot boot путь\к\firstboot-paneltype.img
```

### Reboot to Android
Your device should reboot by itself after +- 10 minutes of waiting, if it actually boots to Windows, complete the Windows setup and then press **Restart** in the start menu to boot back to Android for the last step.

## [Последний шаг: Настройка двойной загрузки](dualboot-ru.md)
