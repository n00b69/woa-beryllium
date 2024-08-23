<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Получение root-прав

### Требования 
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

### Копирование boot образа на Android
- Подключите телефон к компьютеру (с включенной отладкой по USB).
- Щелкните по запросу на телефоне, чтобы разрешить компьютеру доступ к данным телефона. Если запрос не появился, перейдите на панель уведомлений и щелкните уведомление USB, затем измените тип подключения на **передача файлов**.
- Скопируйте файл **boot.img** из папки **platform-tools** во внутреннюю память.

#### Патч boot образа
- Загрузите и установите **Magisk**, затем откройте его.
- Нажмите **Установить** > **Пропатчить boot-образ** и выберите **boot.img**, который вы только что скопировали.
- После завершения исправления найдите **magisk_patched-27000_XXXX.img** в папке **Загрузки** и скопируйте его в папку **platform-tools** на компьютере.

### Перезагрузка в режим fastboot
```cmd
adb reboot bootloader
```

#### Перепрошивка boot образа загрузки с root правами
> Замените `path\to\magisk_patched.img` на ваш путь к образу
```cmd
fastboot flash boot path\to\magisk_patched.img
```

### Перезагрузка в Android
```cmd
fastboot reboot
```

#### Завершение настройки
- Снова откройте приложение **Magisk**.
- Следуйте инструкциям на экране, и ваше устройство должно перезагрузиться через несколько секунд.

### Скопируйте патченый boot образ
> После загрузки устройства

- На экране вашего телефона вероятно появится запрос суперпользователя на использование Shell. Если это произойдет, предоставьте ему доступ.
```cmd
adb shell "su -c cp /dev/block/by-name/boot /sdcard/rooted_boot.img" & adb pull /sdcard/rooted_boot.img
```

## [Следующий шаг: Установка Windows](3-install-ru.md)














