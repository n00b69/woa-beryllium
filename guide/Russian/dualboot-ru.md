<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Dualboot guide

### Требования
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [Образ UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

- [Приложение WOA Helper](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)

- [Switch To Android пакет](https://github.com/n00b69/woa-beryllium/releases/download/Dualboot/beryllium-sta.zip)

## Руководство по двойной загрузке
В этом руководстве предполагается, что у вас есть root-права, если это не так, пожалуйста, сначала следуйте [этому руководству](root-ru.md).

### Установка - Android
- Загрузите и установите приложение WOA Helper, затем откройте его и предоставьте ему root-доступ.
- Загрузите изображение UEFI для вашей панели и поместите его в папку с именем `UEFI` в вашем внутреннем хранилище.
- Нажмите кнопку `Mount Windows` чтобы смонтировать Window в вашем внутреннем хранилище по адресу `/sdcard/Windows`
> [!Important]
> If `/sdcard/Windows` is empty, your rom does not support mounting and you will have to make a boot.img backup inside the app, then copy it manually to Windows once you boot to it (for example by uploading it somewhere and then downloading it while booted into Windows). The same applies to the STA files.
>
> Do the same thing if the folder is read-only.
- Создайте папку с именем `sta` в Windows и распакуйте два файла из файла `Switch to Android package` сдесь (файлы должны находится в `/sdcard/Windows/sta`

- Вернитесь в приложение WOA Helper и нажмите кнопку `Quick boot`.
  
### Установка - Windows
- Перейдите к C:\sta и создайте ярлык `sta.exe` на своём рабочем столе.

#### Загрузка на Android
- Запустите новый ярлык на своем рабочем столе (вы также можете прикрепить его к меню "Пуск" / панели задач для удобства доступа).

#### Загрузка в Windows
- Нажмите `Quick boot` внутри приложения или воспользуйтесь недавно созданным переключателем на панели быстрых настроек
  
## Готово!


