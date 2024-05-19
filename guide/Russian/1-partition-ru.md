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

#### Прошейте OFOX recovery
> Откройте окно CMD внутри папки platform-tools, затем (пока ваш телефон находится в режиме fastboot) выполните 
```cmd
fastboot flash recovery путь\к\ofox-beryllium.img reboot recovery
```

#### Backing up important files
> This will back up **fsc**, **fsg**, **modemst1** and **modemst2** to the current path your CMD is opened in (for example **C:\platform-tools**). Confirm these files are actually there before proceeding.
>
> If you've got anything else you want to back up, do this now. Your Android data will be erased in the next steps.
```cmd
adb shell "dd if=/dev/block/by-name/fsc of=/tmp/fsc" || true && adb pull /tmp/fsc || true && adb shell "dd if=/dev/block/by-name/fsg of=/tmp/fsg" || true && adb pull /tmp/fsg || true && adb shell "dd if=/dev/block/by-name/modemst1 of=/tmp/modemst1" || true && adb pull /tmp/modemst1 || true && adb shell "dd if=/dev/block/by-name/modemst2 of=/tmp/modemst2" || true && adb pull /tmp/modemst2
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










