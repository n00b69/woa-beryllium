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

### Uruchom skrypt partycjonowania
> Zastąp **$** ilością miejsca, jaką ma mieć system Windows (nie dodawaj GB, po prostu wpisz liczbę)
> 
> Jeśli poprosi Cię o ponowne uruchomienie, zrób to
```cmd
adb shell partition $
```

#### Sprawdzanie typu panelu dotykowego
> Zapamiętaj (**Tianma** lub **EBBG**), będziesz go potrzebować w dalszej części instrukcji
```cmd
adb shell panel
```

#### Sprawdź, czy Android nadal się uruchamia
- Po prostu uruchom ponownie telefon i sprawdź, czy Android nadal działa

## [Następny krok: Rootowanie telefonu](2-root.md)





















