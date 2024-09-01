<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Dualboot гайд

### Требования
- [Образ UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

- [Приложение WOA Helper](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)

## Руководство по настройке двойной загрузки
В этом руководстве предполагается, что у вас есть root-права, если это не так, пожалуйста, сначала следуйте [этому руководству](root-ru.md).

### Установка - Android
- Загрузите и установите приложение **WOA Helper**, затем откройте его и предоставьте ему root-доступ.
- Загрузите изображение **UEFI** и поместите его в папку с именем `UEFI` в вашем внутреннем хранилище.
- Вернитесь в приложение WOA Helper и нажмите кнопку **БЫСТРАЯ ЗАГРУЗКА В WINDOWS**.
  
### Установка - Windows
> [!Tip]
> Если вы загружаете Windows впервые и хотите пропустить вход в учетную запись Microsoft, нажмите кнопку **У меня нет интернета** на странице Wi-Fi, а затем при появлении соответствующего запроса нажмите кнопку **Продолжить с ограниченной настройкой**.

#### Загрузка на Android
- Запустите новый ярлык на своем рабочем столе (вы также можете прикрепить его к меню "Пуск" / панели задач для удобства доступа).

#### Загрузка в Windows
- Нажмите **БЫСТРАЯ ЗАГРУЗКА В WINDOWS** в приложении или воспользуйтесь только что созданным переключателем на панели быстрых настроек.

> [!Important]
> If you ever update or change your Android ROM, make sure to create a new **boot.img** backup (after rooting your phone!) and place it inside the **C:\ folder** in Windows, overwriting the old file.
>
> You can use the **BACK UP BOOT IMAGE** feature in the WOA Helper app to do so.

## Готово!


























