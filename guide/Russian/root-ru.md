<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Root guide

### Требования 
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Modded OFOX recovery](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Запустите OFOX
> Если ваше recovery было заменено на стоковое, прошейте его ещё раз в fastboot с помощью:
```cmd
fastboot flash recovery path\to\ofox-beryllium.img reboot recovery 
```

#### Создайте резервную копию вашего загрузочного образа
> Иногда прошивка Magisk может вызвать bootloop. Чтобы исправить это, вам нужно будет восстановить резервную копию boot.img.

Используйте функцию резервного копирования TWRP для создания резервной копии загрузочного раздела.

### Прошивка Magisk
- Прошейте файл magisk.apk (возможно, вам придется переименовать его в magisk.zip) и перезагрузите телефон.
- Следуйте приведенным инструкциям. Выберите метод автоматической установки, если вам предлагается несколько способов.

Теперь ваш телефон перезагрузится, и вы успешно рутируете его.

> [!IMPORTANT]
> После рутинга телефона создайте новую резервную копию boot.img в Android и Windows (с помощью приложения WOA Helper) и удалите все старые резервные копии boot.img, которые вы создали ранее. Если вы этого не сделаете, при переходе на Android ваш рут будет удалён.
> 
> После обновления или изменения вашего ПЗУ (и рутинга) вам нужно будет повторить все шаги, описанные на этой странице.

## Готово!
