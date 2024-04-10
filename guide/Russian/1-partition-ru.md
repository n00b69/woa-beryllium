<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Запуск Windows на Xiaomi Pocophone F1

## Разметка устройства 

### Требования 
- Мозг (самый важный из всех)

- [Android platform tools](https://developer.android.com/studio/releases/platform-tools)
  
- [TWRP](https://github.com/n00b69/woa-beryllium/releases/download/Recoveries/twrp.img)

- [Parted](https://github.com/n00b69/woa-beryllium/releases/download/Files/parted)

### Заметки 
> [!WARNING]  
> Не выполняйте одну и ту же команду дважды, если не указано иное.
> 
> НЕ ПЕРЕЗАГРУЖАЙТЕ ТЕЛЕФОН! Если вы считаете, что допустили ошибку, обратитесь за помощью в [Telegram чате](https://t.me/WinOnF1).
> 
> Не выполняйте все команды сразу, выполняйте их по порядку!
>
> ВЫ МОЖЕТЕ СЛОМАТЬ СВОЕ УСТРОЙСТВО С ПОМОЩЬЮ ПРИВЕДЕННЫХ НИЖЕ КОМАНД, ЕСЛИ БУДЕТЕ ВЫПОЛНЯТЬ ИХ НЕПРАВИЛЬНО!!!

#### Прошейте TWRP recovery
> Откройте окно CMD внутри папки platform-tools, затем (пока ваш телефон находится в режиме fastboot) выполните 
```cmd
fastboot flash recovery "путь\к\twrp.img" reboot recovery
```

```cmd
fastboot reboot recovery
```

#### Сделайте резервное копирование важных файлов
Теперь используйте TWRP для резервного копирования раздела modem и EFS (а также всего остального, если у вас есть важные данные). Переместите эту резервную копию в безопасное место (например, на ваш компьютер), так как последующие действия приведут к удалению ваших данных.

> [!Warning]
> Все ваши данные будут удалены. Это ваш последний шанс создать резервную копию.
> 
> **ЕСЛИ ВЫ ПРОДОЛЖИТЕ РАБОТУ БЕЗ РЕЗЕРВНОГО КОПИРОВАНИЯ modem И EFS, ТО В СЛУЧАЕ НЕУДАЧИ ОТВЕТСТВЕННОСТЬ ЛЕЖИТ НА ВАС**

### Руководство по разметке
> Ваш Pocophone F1 может иметь разный объем памяти. В данном руководстве в качестве примера используются значения для модели емкостью 128 ГБ. При необходимости в руководстве будет указано, можно или нужно ли использовать другие значения.

#### Размантируйте data
- Перейдите к `Монтировать` в TWRP и размонтируйте Data, если она смонтирована

#### Подгатовка к разметке 
> Скачайте файл parted и переместите его в папку platform-tools, затем запустите
```cmd
adb push parted /cache/ && adb shell "chmod 755 /cache/parted" && adb shell /cache/parted /dev/block/sda
```

#### Отобразить текущую таблицу разделов
> Parted выведет список разделов, userdata должна быть последним разделом в списке.
```cmd
print
```

#### Удалите userdata
> Замените `**$**` номером раздела `**userdata**`, должен быть `**21**`
```cmd
rm $
```

#### Recreating userdata
> Replace **1611MB** with the former start value of **userdata** which we just deleted (it is probably 1611MB)
>
> Replace **32GB** with the end value you want **userdata** to have
```cmd
mkpart userdata ext4 1611MB 32GB
```

#### Creating ESP partition
> Replace **32.16GB** with the end value of **userdata**
>
> Replace **32.66GB** with the value you used before, adding **0.5GB** to it
```cmd
mkpart esp fat32 32.16GB 32.66GB
```

#### Creating Windows partition
> Replace **32.66GB** with the end value of **esp**
>
> Replace **123GB** with the end value of your disk, use `p free` to find it
```cmd
mkpart win ntfs 32.66GB 123GB
```

#### Making ESP bootable
> Use `print` to see all partitions. Replace "$" with your ESP partition number, which should be 22
```cmd
set $ esp on
```

#### Exit parted
```cmd
quit
```

#### Formatting data
- Format all data in TWRP, or Android will not boot.
- (Go to Wipe > Format data > type yes)

#### Check if Android still starts
- Just restart the phone, and see if Android still works


## [Next step: Installing Windows](/guide/2-install.md)
