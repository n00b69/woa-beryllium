<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Tworzenie partycji

### Wymagania
- Mózg (najważniejsze ze wszystkich)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Modded OFOX recovery](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Informacje
> [!Warning]  
> Nie uruchamiaj tego samego polecenia dwa razy, chyba że określono inaczej.
> 
> NIE URUCHAMIAJ PONOWNIE TELEFONU! Jeśli uważasz, że popełniłeś błąd, poproś o pomoc na [czacie telegramowym](https://t.me/WinOnF1).
> 
> Nie uruchamiaj wszystkich poleceń na raz, wykonuj je po kolei!

### Flashuj zmodyfikowane recovery OFOX
> Otwórz okno CMD w folderze platform-tools, a następnie (gdy telefon jest w trybie fastboot) uruchom
```cmd
fastboot flash recovery path\to\ofox-beryllium.img reboot recovery
```

#### Tworzenie kopii zapasowych ważnych plików
Użyj OFOX teraz, aby wykonać kopię zapasową modemu i partycji EFS (a także czegokolwiek innego, jeśli masz ważne dane). Przenieś tę kopię zapasową w bezpieczne miejsce (np. na swój komputer), ponieważ kolejne kroki spowodują wyczyszczenie danych.
> [!Warning]
> Wszystkie Twoje dane zostaną usunięte. To Twoja ostatnia szansa na wykonanie kopii zapasowej.
> 
> **JEŚLI KONTYNUUJESZ BEZ KOPII ZAPASOWEJ MODEMU I EFS JEST DUŻE RYZYKO ZE TELEFON NIE BĘDZIE MOGŁ UŻYWAĆ LTE LUB POŁĄCZEŃ**

### Uruchom skrypt partycjonowania
> Zastąp **$** ilością miejsca, jaką ma mieć system Windows (nie dodawaj GB, po prostu wpisz liczbę)
> 
> Jeśli poprosi Cię o ponowne uruchomienie, zrób to
```cmd
adb shell partition $
```

#### Sprawdzanie typu panelu dotykowego
> Zapamiętaj (Tianma lub EBBG), będziesz go potrzebować w dalszej części instrukcji
```cmd
adb shell panel
```

#### Sprawdź, czy Android nadal się uruchamia
- Po prostu uruchom ponownie telefon i sprawdź, czy Android nadal działa


## [Następny Krok](2-install.md)





















