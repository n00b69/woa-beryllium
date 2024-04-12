<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Обновление драйверов 

### Требования
- [Android platform tools](https://developer.android.com/studio/releases/platform-tools)
  
- [Драйвера](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)

- [Скрипт исправления сенсорного экрана](https://github.com/n00b69/woa-beryllium/releases/download/Files/touchfix.bat)
  
- [Образ UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

### Запуск UEFI
> Замените **<путь\к\beryllium-uefi.img>** путём к образу UEFI 
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

#### Отобразить разделы устройства
> Чтобы отобразить список всех подключенных разделов, используйте
```cmd
list volume
```

#### Выберите раздел Windows 
> Замените `$` номером раздела **WINF1**
```cmd
select volume $
```

#### Привязать букву к WINF1
```cmd
assign letter X
```

### Выйти из diskpart
```cmd
exit
```

### Установка драйверов 
> Распакуйте архив с драйверами, затем откройте файл `OfflineUpdater.cmd`

> Введите букву диска **WINF1**, должна быть X, затем нажмите enter

#### Исправить touch
> Запустите файл `touchfix.bat` от имени администратора, иначе сенсорное управление не будет работать при загрузке в Windows

#### Загрузка обратно в Windows
> Перезагрузите устройство, чтобы снова загрузиться в Windows. Если после этого планшет загрузится в Android, перепрошейте образ UEFI с помощью fastboot или с помощью приложения WOA Helper


## Готово!
