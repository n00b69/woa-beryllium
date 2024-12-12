<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Установка Windows

### Требования
- [Модифицированный OFOX](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

- [Образ ARM Windows](https://arkt-7.github.io/woawin/)
  
- [Драйвера](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)

- [Образ UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

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
> НЕ УДАЛЯЙТЕ, НЕ СОЗДАВАЙТЕ И НЕ ИЗМЕНЯЙТЕ КАКИМ-ЛИБО ИНЫМ ОБРАЗОМ РАЗДЕЛЫ, НАХОДЯСЬ В DISKPART!!! ЭТО МОЖЕТ ПРИВЕСТИ К УДАЛЕНИЮ UFS ИЛИ НЕВОЗМОЖНОСТИ ЗАГРУЗКИ В FASTBOOT!!! ЭТО ОЗНАЧАЕТ, ЧТО ВАШЕ УСТРОЙСТВО БУДЕТ ОКИРПИЧЕНО БЕЗ КАКОГО-ЛИБО РЕШЕНИЯ! (за исключением доставки устройства в Xiaomi или его перепрошивки с помощью [EDL](edl-ru.md))
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
> [!Warning]
> НЕ ИСПОЛЬЗУЙТЕ 24H2!!!

> Замените `путь\к\install.esd` актуальным путём к install.esd (файл также может называться install.wim или 22631.2861.XXXXXXX.esd)
```cmd
dism /apply-image /ImageFile:путь\к\install.esd /index:6 /ApplyDir:X:\
```

> Если вы получите `Error 87`, проверьте индекс вышего образа используя `dism /get-imageinfo /ImageFile:путь\к\install.esd`, затем замените `index:6` действтельным индексом **Windows 11 Pro** в вашем образе

### Копирование вашего boot.img в Windows
- Перетащите **rooted_boot.img** на диск **WINF1** в проводнике Windows, затем переименуйте его в **boot.img**.

### Установка драйверов
- Распакуйте пакет драйверов, затем откройте файл `OfflineUpdater.cmd` (Если появляется ошибка, запустите `OfflineUpdaterFix.cmd`)

> Введите букву диска **WINF1** (должна быть **X**) затем нажмите Enter

#### Создайте файлы загрузчика Windows
> Если возникнет какая-либо ошибка, например "Сбой при инициализации системного тома библиотеки", снова откройте `diskpart` и назначьте **ESPF1** любую новую букву, затем замените букву `Y` в следующих командах на букву, которую вы только что добавили.
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

#### Удалите букву диска для ESP
> Если это не сработает, проигнорируйте это и перейдите к следующей команде. Этот фантомный диск исчезнет при следующей перезагрузке ПК.
```cmd
mountvol y: /d
```

### Перезагрузитесь в fastboot
```cmd
adb reboot bootloader
```

#### Загрузитесь в firstboot.img
> Download **firstboot-paneltype.img** for your device's panel and replace `путь\к\firstboot-paneltype.img` with the actual path to the image
>
> Use `adb shell panel` in the modified recovery if you forgot what panel you have

> [!Important]
> Remove your USB cable right after leaving the fastboot screen, or Windows may crash in the initial setup, which will then require a reinstall
```cmd
fastboot boot путь\к\firstboot-paneltype.img
```

### Перезагрузка в Android
Ваше устройство должно перезагрузиться само после +- 10 минут ожидания, после чего вы загрузитесь в Android для последнего шага.

## [Последний шаг: Настройка двойной загрузки](4-dualboot-ru.md)
