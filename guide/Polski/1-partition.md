<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Tworzenie partycji

### Wymagania
- Odblokowany bootloader

- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Zmodyfikowane recovery OFOX](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Uwagi
> [!Warning]  
> 
> NIE URUCHAMIAJ PONOWNIE TELEFONU! Jeśli uważasz, że popełniłeś błąd, poproś o pomoc na [Telegramie](https://t.me/WinOnF1).
> 
> Nie uruchamiaj wszystkich poleceń na raz, wykonuj je po kolei!

### Otwieranie CMD jako administrator
> Pobierz **platform-tools** i wypakuj gdzieś folder, a następnie otwórz CMD jako **administrator**.
>
> Zaleca się pozostawienie tego okna otwartego i korzystanie z niego przez cały przewodnik.
> 
> Zastąp `ścieżka\do\platform-tools` rzeczywistą ścieżką do folderu platform-tools, na przykład **C:\platform-tools**.
```cmd
cd ścieżka\do\platform-tools
```

> [!Note]
> If your device is not detected in fastboot or recovery mode, you'll have to install USB drivers [using this guide](troubleshooting.md#device-is-not-recognized-in-fastboot-or-recovery)

#### Flashuj zmodyfikowane recovery OFOX
> Otwórz okno CMD w folderze platform-tools, a następnie (gdy telefon jest w trybie fastboot) wpisz
```cmd
fastboot flash recovery ścieżka\do\ofox-beryllium.img reboot recovery
```

### Tworzenie kopii zapasowej ważnych plików
> Spowoduje to utworzenie kopii zapasowej plików **fsc**, **fsg**, **modemst1** i **modemst2** w bieżącej ścieżce, w której otwarto CMD (na przykład **C:\platform-tools**). Przed kontynuowaniem upewnij się, że te pliki rzeczywiście tam są.
>
> Trzymaj tę kopię zapasową w bezpiecznym miejscu. Jeśli oprogramowanie Twojego urządzenia kiedykolwiek ulegnie uszkodzeniu, możesz potrzebować tej kopii, gdyż w przeciwnym wypadku telefon może już nigdy nie być w stanie wykonywać połączeń.
> 
> Jeśli chcesz utworzyć kopię zapasową czegoś innego, zrób to teraz. Twoje dane Androida zostaną usunięte w kolejnych krokach.
```cmd
cmd /c "for %i in (fsg,fsc,modemst1,modemst2) do (adb shell dd if=/dev/block/by-name/%i of=/tmp/%i.bin & adb pull /tmp/%i.bin)"
```

#### Tworzenie kopii zapasowych obrazu rozruchu
> Spowoduje to utworzenie kopii zapasowej obecnego obrazu rozruchu w bieżącej ścieżce
```cmd
adb pull /dev/block/by-name/boot boot.img
```

#### Sprawdzanie typu panelu dotykowego
> Zapamiętaj (**Tianma** lub **EBBG**), będziesz go potrzebować w dalszej części instrukcji
```cmd
adb shell panel
```

### Przewodnik dotyczący partycjonowania
> There are two methods to partition your device. Please select the method you would like to use below. 

#### Method 1: Manual partitioning 

<details>
  <summary><strong>Click here for method 1</strong></summary> 

#### Odmontuj dane
> Ignore any possible errors and continue
```cmd
adb shell umount /dev/block/by-name/userdata
``` 

#### Przygotowanie do partycjonowania
```cmd
adb shell parted /dev/block/sda
``` 

#### Wyświetlanie aktualnej tablicy partycji
> Parted wyświetli listę partycji, **userdata** powinenen być ostatnią partycją na liście.
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
> Zastąp **32GB** wartością końcową, jaką chcesz mieć dla **userdata**. In this example your available usable space in Android will be 32GB-1611MB = **30GB**
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
```cmd
mkpart win ntfs 32.3GB -0MB
``` 

#### Tworzenie bootowalnego ESP
> Użyj `print`, aby zobaczyć wszystkie partycje. Zamień "$" na numer partycji ESP, który powinien wynosić **22**
```cmd
set $ esp on
``` 

#### Wyjdź z parted
```cmd
quit
``` 

### Formatowanie danych
- Sformatuj wszystkie dane w TWRP, w przeciwnym razie Android nie uruchomi się.
- (Idź do Wyczyść > Formatuj dane > wpisz yes) 

#### Sprawdź, czy Android nadal się uruchamia
- Po prostu uruchom ponownie telefon i sprawdź, czy Android nadal działa 

### Formatting Windows and ESP drives
> Reboot into the modded recovery, then run the below two commands
```cmd
adb shell mkfs.ntfs -f /dev/block/by-name/win -L WINF1
``` 

```cmd
adb shell mkfs.fat -F32 -s1 /dev/block/by-name/esp -n ESPF1
``` 

</details> 

#### Method 2: Automatic partitioning 

<details>
  <summary><strong>Click here for method 2</strong></summary>

### Uruchom skrypt partycjonowania
> Zastąp **$** ilością miejsca, jaką ma mieć system Windows (nie dodawaj GB, po prostu wpisz liczbę)
> 
> Jeśli poprosi Cię o ponowne uruchomienie, zrób to
```cmd
adb shell partition $
```

#### Sprawdź, czy Android nadal się uruchamia
- Po prostu uruchom ponownie telefon i sprawdź, czy Android nadal działa

</details>

## [Następny krok: Rootowanie telefonu](2-root.md)





















