<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Разметка устройства 

### Требования 
- Мозг (самый важный из всех)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Модифицированный OFOX recovery](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Примечание:
> [!WARNING]  
> Не выполняйте одну и ту же команду дважды, если не указано иное.
> 
> НЕ ПЕРЕЗАГРУЖАЙТЕ ТЕЛЕФОН! Если вы считаете, что допустили ошибку, обратитесь за помощью в [Telegram чате](https://t.me/WinOnF1).
> 
> Не выполняйте все команды сразу, выполняйте их по порядку!
>
> ВЫ МОЖЕТЕ ОКИРПИЧИТЬ СВОЁ УСТРОЙСТВО ИСПОЛЬЗУЯ ПРИВЕДЁННЫЕ НИЖЕ КОМАНДЫ, ЕСЛИ БУДЕТЕ ВЫПОЛНЯТЬ ИХ НЕПРАВИЛЬНО!!!

#### Прошейте OFOX recovery
> Откройте окно CMD внутри папки platform-tools, затем (пока ваш телефон находится в режиме fastboot) выполните 
```cmd
fastboot flash recovery путь\к\ofox-beryllium.img reboot recovery"
```

#### Сделайте резервное копирование важных файлов
Теперь используйте OFOX для резервного копирования раздела modem и EFS (а также всего остального, если у вас есть важные данные). Переместите эту резервную копию в безопасное место (например, на ваш компьютер), так как последующие действия приведут к удалению ваших данных.

> [!Warning]
> Все ваши данные будут удалены! Это ваш последний шанс создать резервную копию!
> 
> **ЕСЛИ ВЫ ПРОДОЛЖИТЕ РАБОТУ БЕЗ РЕЗЕРВНОГО КОПИРОВАНИЯ modem И EFS, ТО В СЛУЧАЕ НЕУДАЧИ ОТВЕТСТВЕННОСТЬ ЛЕЖИТ НА ВАС!**

### Run the partitioning script
> Replace **$** with the amount of storage you want Windows to have (do not add GB, just write the number)
> 
> If it asks you to run it once again, do so
```cmd
adb shell partition $
```

#### Checking your panel type
> Remember the output (Tianma or EBBG), you will need this later in the guide
```cmd
adb shell panel
```

### Проверьте, запускается ли Android 
- Просто перезагрузите телефон и посмотрите, загружается ли Android

## [Следующий шаг: Установка Windows](2-install-ru.md)










