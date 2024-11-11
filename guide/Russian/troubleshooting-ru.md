<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Исправление Проблем 
> Ниже вы найдете список распространенных проблем и путей их решения

## LTE and other network services in Android no longer work
> Sometimes Windows may wipe your modem partitions, resulting in the loss of LTE in Android. To fix this, you'll need to restore your modem using the backups that you hopefully made [while partitioning your device](1-partition.md#backing-up-important-files). If you did not do this step, there is likely no way to recover.
- Boot into any recovery other than the stock recovery (ADB commands do not work there)
- Open CMD in the **platform-tools** folder.
- Restore the four partitions that you backed up using the below commands. Replace `path\to` with the actual path of the images.
```cmd
adb push path\to\fsc.bin /cache/ & adb shell dd if=/cache/fsc.bin of=/dev/block/by-name/fsc
```

```cmd
adb push path\to\fsg.bin /cache/ & adb shell dd if=/cache/fsg.bin of=/dev/block/by-name/fsg
```

```cmd
adb push path\to\modemst1.bin /cache/ & adb shell dd if=/cache/modemst1.bin of=/dev/block/by-name/modemst1
```

```cmd
adb push path\to\modemst2.bin /cache/ & adb shell dd if=/cache/modemst2.bin of=/dev/block/by-name/modemst2
```
- Reboot your device and check if LTE works.
> [!Note]
> If it still does not work, you will have to do some additional steps;
- Download the [stock rom for your device](https://xmfirmwareupdater.com/miui/beryllium/)
- Open it, look for a file called **modem.img** and extract it.
- Boot into fastboot mode (`adb reboot bootloader`).
- Flash this **modem.img** with the below command, replacing `path\to\modem.img` with the actual path of the image
```cmd
fastboot flash modem path\to\modem.img
```

##### Finished!

## LTE in Windows does not work
> [!Note]
> You may have to follow the steps above to restore your modem first
- In Android, find your APN settings. It should be located in `Connections` > `Mobile Networks` > `Access Point Names`.
- Write the information of your current APN settings down, then boot into Windows.
- In `Cellular Settings`, click on `Mobile operator settings` > `APN settings` and add the APN settings you wrote down earlier.
- Enable **Cellular**. It may say `No Internet Access`, but it should still work. 

##### Finished!

## Не удается смонтировать Windows в Android
Если при монтировании Windows образуется пустая папка, значит у вас не установлена Windows, либо в вашем ПЗУ нет поддержки монтирования.

##### Готово!

## Не удается выполнить запись в Windows из Android
> Это вызвано выключением Windows вместо её перезапуска.
- Чтобы решить эту проблему, загрузитесь в Windows и затем нажмите "перезагрузка", затем, когда экран выключится, загрузитесь в TWRP и оттуда загрузите Android.
- Или, отключите режим гибернации в Windows используя [этот](https://github.com/n00b69/woa-beryllium/releases/tag/1.0) скрипт 
> В качестве альтернативы, если вы уже настроили приложение Switch to Android, просто используйте его для переключения на Android.

##### Готово!

## USB не работает 
Включите режим USB хост ипользуя инструкцию на странице [полезные приложения и инструкции](materials-ru.md).

##### Готово!

## 0xc000021a BSOD
Обычно это означает, что произошел сбой winlogon.exe, и вам, возможно, потребуется повторно применить образ Windows.

##### Готово!

## Компьютер неожиданно перезагрузился или возникла непредвиденная ошибка
Если вы столкнётесь с этой проблемой, возможно, вам потребуется повторно развернуть образ Windows. Для этого воспользуйтесь [руководством по переустановке](reinstall-ru.md).

##### Готово!

## INACCESSIBLE_BOOT_DEVICE BSOD
Этот синий экран смерти, вероятно, означает сбой в установке какого-либо драйвера. Чтобы исправить это, переустановите драйверы, используя [руководство по переустановке драйверов](update-ru.md).

##### Готово!

