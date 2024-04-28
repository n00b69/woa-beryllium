<img align="right" src="https://github.com/n00b69/woa-equuleus/blob/main/equuleus.png" width="350" alt="Windows 11 running on equuleus">

# Windows na Xiaomi Mi 8 Pro

## Tworzenie partycji

### Wymagania
- Mózg (najważniejsze ze wszystkich)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [TWRP](https://github.com/n00b69/woa-equuleus/releases/download/Files/twrp.img)

- [Parted](https://github.com/n00b69/woa-equuleus/releases/download/Files/parted)

### Notes
> [!Warning]  
> Nie uruchamiaj tego samego polecenia dwa razy, chyba że określono inaczej.
> 
> NIE URUCHAMIAJ PONOWNIE TELEFONU! Jeśli uważasz, że popełniłeś błąd, poproś o pomoc na [czacie telegramowym](https://t.me/woaequuleus).
> 
> Nie uruchamiaj wszystkich poleceń na raz, wykonuj je po kolei!
>
> MOŻESZ ZNISZCZYĆ SWOJE URZĄDZENIE ZA POMOCĄ PONIŻSZYCH POLECEŃ, JEŚLI ZROBISZ JE ŹLE!!!

#### Zflashuj TWRP
> Otwórz okno CMD w folderze platform-tools, a następnie (gdy telefon jest w trybie szybkiego uruchamiania) uruchom
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

#### Tworzenie kopii zapasowych ważnych plików
Użyj TWRP teraz, aby wykonać kopię zapasową modemu i partycji EFS (a także czegokolwiek innego, jeśli masz ważne dane). Przenieś tę kopię zapasową w bezpieczne miejsce (np. na swój komputer), ponieważ kolejne kroki spowodują wyczyszczenie danych.
> [!Warning]
> Wszystkie Twoje dane zostaną usunięte. To Twoja ostatnia szansa na wykonanie kopii zapasowej.
> 
> **JEŚLI KONTYNUUJESZ BEZ KOPII ZAPASOWEJ MODEMU I EFS JEST DUŻE RYZYKO ZE TELEFON NIE BĘDZIE MOGŁ UŻYWAĆ LTE LUB POŁĄCZEŃ**

### Przewodnik dotyczący partycjonowania
> Twój Xiaomi Mi 8 Pro może mieć różne rozmiary pamięci. Ten przewodnik używa wartości modelu 128GB jako przykładu. W razie potrzeby przewodnik wspomni, czy można lub należy użyć innych wartości.

#### Odmontuj dane
- Przejdź do "Montuj" w TWRP i odmontuj dane, jeśli są zamontowane

#### Przygotowanie do partycjonowania
> Pobierz plik parted i przenieś go do folderu platform-tools, a następnie uruchom
```cmd
adb push parted /cache/ && adb shell "chmod 755 /cache/parted" && adb shell /cache/parted /dev/block/sda
```

#### Wyświetlanie aktualnej tablicy partycji
> Parted wyświetli listę partycji, "userdata" powinenen być ostatnią partycją na liście.
```cmd
print
```

#### Usuwanie userdata
> Zamień **$** na numer partycji **userdata**, który powinien wynosić **21**
```cmd
rm $
```

#### Ponowne utworzenie userdata
> Zamień **1611MB** na poprzednią wartość początkową **userdata**, którą właśnie usunęliśmy (prawdopodobnie jest to 1611MB)
>
> Zastąp **32GB** wartością końcową, jaką chcesz mieć dla **userdata**
```cmd
mkpart userdata ext4 1611MB 32GB
```

#### Tworzenie partycji ESP 
> Zamień **32GB** na końcową wartość **userdata**
>
> Zastąp **32.3GB** wartością, której użyłeś wcześniej, dodając do niej **0.3GB**
```cmd
mkpart esp fat32 32GB 32.3GB
```

#### Tworzenie partycji Windows
> Zastąp **32.3GB** wartością końcową **esp**
>
> Zamień **123GB** na końcową wartość dysku, użyj `p free`, aby go znaleźć
```cmd
mkpart win ntfs 32.3GB 123GB
```

#### Tworzenie bootowalnego ESP
> Użyj `print`, aby zobaczyć wszystkie partycje. Zamień „$” na numer partycji ESP, który powinien wynosić 22
```cmd
set $ esp on
```

#### Wyjdź z parted
```cmd
quit
```

#### Formatowanie danych
- Sformatuj wszystkie dane w TWRP, w przeciwnym razie Android nie uruchomi się.
- (Idź do Wyczyść > Formatuj dane > wpisz yes)

#### Sprawdź, czy Android nadal się uruchamia
- Po prostu uruchom ponownie telefon i sprawdź, czy Android nadal działa


## [Następny Krok](2-install.md)





















