<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Разметка устройства 

### Требования 
- Мозг (самый важный из всех)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Модифицированный OFOX recovery](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Примечание:
> [!WARNING]  
> 
> НЕ ПЕРЕЗАГРУЖАЙТЕ ТЕЛЕФОН! Если вы считаете, что допустили ошибку, обратитесь за помощью в [Telegram чате](https://t.me/WinOnF1).
> 
> Не выполняйте все команды сразу, выполняйте их по порядку!
>
> ВЫ МОЖЕТЕ ОКИРПИЧИТЬ СВОЁ УСТРОЙСТВО ИСПОЛЬЗУЯ ПРИВЕДЁННЫЕ НИЖЕ КОМАНДЫ, ЕСЛИ БУДЕТЕ ВЫПОЛНЯТЬ ИХ НЕПРАВИЛЬНО!!!

### Открыть CMD от имени администратора
> Скачайте **platform-tools** и распакуйте его куда-нибудь, затем откройте CMD от имени **администратора**.
>
> Рекомендуется держать CMD открытым и использовать его на протяжении всего руководства.
> 
> Замените `путь\к\platform-tools` на путь к папке platform-tools, например **C:\platform-tools**.
```cmd
cd путь\к\platform-tools
```

#### Прошейте OFOX recovery
> Откройте окно CMD внутри папки platform-tools, затем (пока ваш телефон находится в режиме fastboot) выполните 
```cmd
fastboot flash recovery путь\к\ofox-beryllium.img reboot recovery
```

#### Создание резервной копии важных файлов
> Это создаст бэкап **fsc**, **fsg**, **modemst1** и **modemst2** в текущем расположении, где открыта ваша командная строка (например **C:\platform-tools**). Убедитесь, что эти файлы действительно сдесь, прежде чем продолжить.
>
> Если вы хотите создать резервную копию чего-либо ещё, сделайте это сейчас. Ваши данные в Android будут удалены в ходе следующих действий.
```cmd
cmd /c "for %i in (fsg,fsc,modemst1,modemst2) do (adb shell dd if=/dev/block/by-name/%i of=/tmp/%i.bin & adb pull /tmp/%i.bin)"
```

### Запустите скрипт разметки 
> Замените **$** объёмом памяти, который вы хотите выделить для Windows (не добавляйте ГБ, просто введите число).
> 
> Если скрипт попросит запустить его ещё раз, то так и сделайте
```cmd
adb shell partition $
```

#### Узнайте тип вашего дисплея 
> Запомните вывод (**Tianma** or **EBBG**), это понадобится вам позже
```cmd
adb shell panel
```

### Проверьте, запускается ли Android 
- Просто перезагрузите телефон и посмотрите, загружается ли Android

## [Следующий шаг: Установка Windows](2-install-ru.md)










