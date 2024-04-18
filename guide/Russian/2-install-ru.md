<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Установка Windows

### Требования
- [образ ARM Windows](https://worproject.com/esd)
  
- [Драйвера](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)

- [Скрипт исправления touch](https://github.com/n00b69/woa-beryllium/releases/download/Files/touchfix.bat)
  
- [Образ UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

### Загрузитесь в UEFI
> Замените **<путь\к\beryllium-uefi.img>** актуальным путём к образу UEFI
```cmd
fastboot boot <путь\к\beryllium-uefi.img>
```

#### Включите режим mass storage
> После загрузки в UEFI используйте кнопки регулировки громкости для навигации по меню и кнопку питания для подтверждения
- Выберите **UEFI Boot Menu**.
- Выберите **USB Attached SCSI (UAS) Storage**.
- Нажмите кнопку **питания** дважды чтобы подтвердить.

### Diskpart
> [!WARNING]
> НЕ УДАЛЯЙТЕ, НЕ СОЗДАВАЙТЕ И НЕ ИЗМЕНЯЙТЕ КАКИМ-ЛИБО ИНЫМ ОБРАЗОМ РАЗДЕЛЫ, НАХОДЯСЬ В DISKPART!!! ЭТО МОЖЕТ ПРИВЕСТИ К УДАЛЕНИЮ UFS ИЛИ НЕВОЗМОЖНОСТИ ЗАГРУЗКИ В FASTBOOT!!! ЭТО ОЗНАЧАЕТ, ЧТО ВАШЕ УСТРОЙСТВО БУДЕТ ОКИРПИЧЕНО БЕЗ КАКОГО-ЛИБО РЕШЕНИЯ! (за исключением доставки устройства в Xiaomi или его перепрошивки с помощью EDL, и то, и другое, скорее всего, будет стоить денег)
```cmd
diskpart
```

#### Найдите ваш телефон
> При этом отобразится список всех подключенных дисков
```cmd
lis dis
```

#### Выберите диск вашего телефона
> Замените `$` актуальным номером диска вашего телефона (должен быть последним в списке)
```cmd
sel dis $
```

#### Отобразите список разделов
> Это отобразит список разделов вашего телефона 
```cmd
lis par
```

#### Выберите раздел Windows 
> Замените `$` номером раздела Windows (должен быть 23)
```cmd
sel par $
```

#### Отформатируйте раздел Windows
```cmd
format quick fs=ntfs label="WINF1"
```

#### Добавьте букву к разделу Windows
```cmd
assign letter X
```

#### Выберите раздел ESP
> Замените `$` номером раздела ESP (должен быть 22)
```cmd
sel par $
```

#### Отформатируйте раздел ESP
```cmd
format quick fs=fat32 label="ESPF1"
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
> Замените `<путь\к\install.esd>` актуальным путём к install.esd (файл также может называться install.wim)
```cmd
dism /apply-image /ImageFile:<путь\к\install.esd> /index:6 /ApplyDir:X:\
```

> Если вы получите `Error 87`, проверьте индекс вышего образа используя `dism /get-imageinfo /ImageFile:<путь\к\install.esd>`, затем замените `index:6` действтельным индексом Windows 11 Pro в вашем образе

### Установка драйверов
> Распакуйте пакет драйверов, затем откройте файл `OfflineUpdater.cmd` 

> Введите букву диска **WINF1** (должна быть **X**) затем нажмите Enter

#### Исправить touch
> Запустите файл `touchfix.bat` от имени администратора, иначе сенсор не будет работать при загрузке в Windows
  
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
```diskpart
select volume $
```

#### Отвяжите букву X
```diskpart
remove letter x
```

#### Выберите раздел ESP телефна
> Используйте `list volume` чтобы найти его, замените `$` номером раздела **ESPF1**
```diskpart
select volume $
```

#### Отвяжите букву Y
```diskpart
remove letter y
```

#### Выйдите из diskpart
```diskpart
exit
```

### Перезагрузка в Android
> Чтобы настроить двойную загрузку

#### Проверьте тип дисплея 
> Это должно отобразить `dsi_ebbg_fhd_ft8719_video_display` или `dsi_tianma_fhd_nt36672a_video_display`
```cmd
adb shell dmesg | grep dsi_display_bind
```
Запомните тип вашего дисплея (Tianma или EBBG), это понадобится вам позже

## [Последний шаг: Настройка двойной загрузки](dualboot-ru.md)
