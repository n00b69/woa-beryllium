<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Instalacja Windowsa

### Wymagania
- [Windows dla ARM](https://worproject.com/esd)
  
- [Sterowniki](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)
  
- [Modded OFOX recovery](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

### Boot to OFOX recovery
> If your recovery has been replaced by the stock recovery, flash it again using
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

#### Włączanie trybu pamięci masowej
> If it asks you to run it once again, do so
```cmd
adb shell msc
```

### Diskpart
> [!WARNING]
> NIE USUWAJ ŻADNYCH PARTYCJI W DISKPART!!!! TO USUNIE CAŁĄ TWOJĄ UFS!!!! OZNACZA TO, ŻE TWOJE URZĄDZENIE ZOSTANIE TRWAŁE USZKODZONE BEZ ROZWIĄZANIA! (z wyjątkiem zabrania urządzenia do Xiaomi lub flashowania go za pomocą EDL, co prawdopodobnie będzie kosztować)
```cmd
diskpart
```

#### Wybór partycji Windows
> Use `list volume` to find it, replace `$` with the actual number of **WINF1**
```diskpart
select volume $
```

#### Dodaj literę do systemu Windows
```cmd
assign letter x
```

#### Wybieranie Partycji ESP
> Use `list volume` to find it, replace `$` with the actual number of **ESPF1**
```diskpart
select volume $
```

#### Dodaj literę do ESP
```cmd
assign letter y
```

#### Wyjdź z Diskpart
```cmd
exit
```

### Instalowanie Windowsa
> Zamień `<path\to\install.esd>` na rzeczywistą ścieżkę do pliku install.esd (może on również nosić nazwę install.wim)

```cmd
dism /apply-image /ImageFile:<path\to\install.esd> /index:6 /ApplyDir:X:\
```

> Jeśli pojawi się komunikat `Błąd 87`, sprawdź indeks obrazu za pomocą polecenia `dism /get-imageinfo /ImageFile:<path\to\install.esd>`, a następnie zastąp `index:6` rzeczywistym numerem indeksu systemu Windows 11 Pro na Twoim obrazie

### Instalowanie Sterowników
> Wypakuj archiwum ze sterownikami, potem otwórz plik `OfflineUpdater.cmd`
 
> Jeśli poprosi Cię o podanie litery, wpisz literę dysku **WINF1** (która powinna być X), a następnie naciśnij enter.

#### Utwórz pliki bootloadera systemu Windows
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Włącz tryb testowy
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Wyłączanie odzyskiwania
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" recoveryenabled no
```

#### Wyłączanie sprawdzania integralności
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" nointegritychecks on
```

### Usuń przypisanie litery dysku
> Żeby nie pozostał tam po odłączeniu urządzenia
```cmd
diskpart
```

#### Wybierz partycję systemu Windows w telefonie
> Użyj `list Volume`, aby go znaleźć, zamień `$` na rzeczywistą liczbę **WINF1**
```część dysku
sel vol $
```

#### Usuń przypisanie litery X
```część dysku
remove letter x
```

#### Wybierz głośność systemu ESP w telefonie
> Użyj `list Volume`, aby go znaleźć, zamień `$` na rzeczywistą liczbę **ESPF1**
```część dysku
sel vol $
```

#### Usuń przypisanie litery Y
```część dysku
remove letter y
```

#### Wyjdź z dysku
```część dysku
exit
```

### Uruchom ponownie do Androida
> Uruchom ponownie do Androida aby ustawić dualboot


## [Ostatni Krok: Ustawianie dualboot](dualboot.md)

















