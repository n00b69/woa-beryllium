<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Исправление Проблем 
> Ниже вы найдете список распространенных проблем и путей их решения

## Не удается смонтировать Windows в Android
Если при монтировании Windows образуется пустая папка, значит у вас не установлена Windows, либо в вашем ПЗУ нет поддержки монтирования.

##### Готово!

## Не удается выполнить запись в Windows из Android
> Это вызвано выключением Windows вместо её перезапуска.
- Чтобы решить эту проблему, загрузитесь в Windows и затем нажмите "перезагрузка", затем, когда экран выключится, загрузитесь в TWRP и оттуда загрузите Android.
- Или, отключите режим гибернации в Windows используя [этот]() скрипт 
> Alternatively, if you have already set up the Switch to Android app, simply use this to switch to Android.

##### Готово!

## USB не работает 
Включите режим USB хост ипользуя инструкцию на странице [полезные приложения и инструкции](additional-materials-ru.md).

##### Готово!

## DISM Error:87 The add-driver option is unkown
This usually means that you have an unclean Windows image with some other drivers. You need to get a clean Windows image (which means you didn't follow instructions).

##### Finished!

## 0xc000021a BSOD
This usually means that winlogon.exe has failed, and you may need to reapply the Windows image.

##### Finished!

## The computer restarted unexpectedly or encountered an unexpected error
If you stumble upon this error, you may need to redeploy the Windows image. Use the [reinstall guide](reinstall.md) for this.

##### Finished!

## INACCESSIBLE_BOOT_DEVICE BSOD
This Blue Screen of Death likely means some broken driver installation. To fix this, reinstall the drivers using the [reinstall guide](reinstall.md).

##### Finished!

