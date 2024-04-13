<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Reinstalling Windows

### Требования
- [ARM образ Windows](https://worproject.com/esd)
  
- [Драйвера](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)

- [Скрипт исправления touch](https://github.com/n00b69/woa-beryllium/releases/download/Files/touchfix.bat)
  
- [образ UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

### Загрузка в UEFI
> Замените **<путь\к\beryllium-uefi.img>** с актуальным путём к образу UEFI
```cmd
fastboot boot <путь\к\beryllium-uefi.img>
```

#### Включение режима mass storage
> После загрузки в UEFI используйте кнопки регулировки громкости для навигации по меню и кнопку питания для подтверждения
- Выберите **UEFI Boot Menu**.
- Выберите **USB Attached SCSI (UAS) Storage**.
- Нажмите кнопку **питания** дважды чтобы подтвердить.

### Diskpart
```cmd
diskpart
```

#### Найдите ваш телефон
> При этом отобразится список всех подключенных дисков
```cmd
lis dis
```

#### Выберите ваш телефон
> Замените `$` актуальным номером вашего телефона (должен быть последним)
```cmd
sel dis $
```

#### Отобразить список разделов вашего телефона
> Это отобразит список разделов вашего телефона 
```cmd
lis par
```

#### Выбрать раздел Windows 
> Замените `$` номером раздела Windows (должен быть 23)
```cmd
sel par $
```

#### Добавить букву к разделу Windows
```cmd
assign letter X
```

#### Выйти из diskpart
```cmd
exit
```

#### Formatting Windows
> Go to Windows Explorer > This PC and select **WINF1**. Right click and format as NTFS.

### Установка Windows
> Замените `<путь\к\install.esd>` актуальным путём к install.esd (он также может называться install.wim)
```cmd
dism /apply-image /ImageFile:<путь\к\install.esd> /index:6 /ApplyDir:X:\
```

> Если вы получите `Error 87`, проверьте индекс вышего образа используя `dism /get-imageinfo /ImageFile:<путь\к\install.esd>`, затем замените `index:6` действтельным индексом Windows 11 Pro в вашем образе

### Установка драйверов
> Распакуйте пакет драйверов, затем откройте файл `OfflineUpdater.cmd` 

> Введите букву диска **WINF1**, должна быть X, затем нажмите Enter

#### Исправить touch
> Запустите файл `touchfix.bat` от имени администратора, иначе сенсорное управление не будет работать при загрузке в Windows

### Boot into Windows
Reboot your phone. If you end up in Android instead of Windows, flash the UEFI again using WOA Helper.

#### Setting up Windows
> Your device will now set up Windows. This will take some time. It will eventually reboot, and after that the initial setup (oobe) should launch.

> [!Note]
> To skip the Microsoft Account login, use "g" for the email and password. Windows will then let you make a local account

## Finished!


















