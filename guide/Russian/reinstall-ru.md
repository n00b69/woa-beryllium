<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Переустановка Windows

### Требования
- [Образ ARM Windows](https://worproject.com/esd)
  
- [Драйвера](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)
  
- [Образ UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

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

#### Выйдите из diskpart
```cmd
exit
```

#### Отформатируйте раздел Windows
> Перейдите в Проводник Windows > Этот компьютер и выберите **WINF1**. Щелкните правой кнопкой мыши и отформатируйте как NTFS.

### Установка Windows
> Замените `<путь\к\install.esd>` актуальным путём к install.esd (файл также может называться install.wim)
```cmd
dism /apply-image /ImageFile:<путь\к\install.esd> /index:6 /ApplyDir:X:\
```

> Если вы получите `Error 87`, проверьте индекс вышего образа используя `dism /get-imageinfo /ImageFile:<путь\к\install.esd>`, затем замените `index:6` действтельным индексом Windows 11 Pro в вашем образе

### Установка драйверов
> Распакуйте пакет драйверов, затем откройте файл `OfflineUpdater.cmd` 

> Введите букву диска **WINF1** (должна быть X) затем нажмите Enter

### Загрузка в Windows
Перезагрузите телефон. Если в итоге он загрузится в Android, а не в Windows, перепрошейте UEFI заново с помощью WOA Helper.

#### Настройка Windows
> Сейчас Windows на вашем устройстве настроится. Это займёт некоторое время. В конечном итоге телефон перезагрузится, и после этого должна запуститься программа начальной установки (oobe).

> [!Note]
> Если вы не хотите входить в учетную запись Майкрософт, введите "g" в качестве адреса электронной почты и пароля. После этого Windows позволит вам создать локальную учетную запись

## Готово!


















