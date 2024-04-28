<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Tworzenie partycji

### Wymagania
- Mózg (najważniejsze ze wszystkich)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Modded OFOX recovery](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Notes
> [!Warning]  
> Nie uruchamiaj tego samego polecenia dwa razy, chyba że określono inaczej.
> 
> NIE URUCHAMIAJ PONOWNIE TELEFONU! Jeśli uważasz, że popełniłeś błąd, poproś o pomoc na [czacie telegramowym](https://t.me/WinOnF1).
> 
> Nie uruchamiaj wszystkich poleceń na raz, wykonuj je po kolei!

### Flash the modded OFOX recovery
> Open a CMD window inside the platform-tools folder, then (while your phone is in fastboot mode) run
```cmd
fastboot flash recovery path\to\ofox-beryllium.img reboot recovery
```

#### Tworzenie kopii zapasowych ważnych plików
Użyj OFOX teraz, aby wykonać kopię zapasową modemu i partycji EFS (a także czegokolwiek innego, jeśli masz ważne dane). Przenieś tę kopię zapasową w bezpieczne miejsce (np. na swój komputer), ponieważ kolejne kroki spowodują wyczyszczenie danych.
> [!Warning]
> Wszystkie Twoje dane zostaną usunięte. To Twoja ostatnia szansa na wykonanie kopii zapasowej.
> 
> **JEŚLI KONTYNUUJESZ BEZ KOPII ZAPASOWEJ MODEMU I EFS JEST DUŻE RYZYKO ZE TELEFON NIE BĘDZIE MOGŁ UŻYWAĆ LTE LUB POŁĄCZEŃ**

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

#### Sprawdź, czy Android nadal się uruchamia
- Po prostu uruchom ponownie telefon i sprawdź, czy Android nadal działa


## [Następny Krok](2-install.md)





















