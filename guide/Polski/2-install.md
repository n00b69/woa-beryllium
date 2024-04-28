<img align="right" src="https://github.com/n00b69/woa-equuleus/blob/main/equuleus.png" width="350" alt="Windows 11 running on equuleus">

# Windows na Xiaomi Mi 8 Pro

## Instalacja Windowsa

### Wymagania
- [Windows dla ARM](https://worproject.com/esd)
  
- [Sterowniki](https://github.com/n00b69/woa-equuleus/releases/tag/Drivers)

- [Devcfg (naprawia dotyk)](https://github.com/n00b69/woa-equuleus/releases/download/Files/devcfg-polaris.img)
  
- [obraz UEFI](https://github.com/n00b69/woa-equuleus/releases/tag/UEFI)

### Uruchom do UEFI
> Zastąp **<path\to\equuleus-uefi.img>** rzeczywistą ścieżką obrazu UEFI
```cmd
fastboot boot <path\to\equuleus-uefi.img>
```

#### Włączanie trybu pamięci masowej
> Po uruchomieniu systemu UEFI użyj przycisków głośności do poruszania się po menu i przycisku zasilania, aby potwierdzić
- Wybierz **UEFI Boot Menu**.
- Wybierz **USB Attached SCSI (UAS) Storage**.
- Naciśnij przycisk dwa razy aby potwierdzić.

### Diskpart
> [!WARNING]
> NIE USUWAJ ŻADNYCH PARTYCJI W DISKPART!!!! TO USUNIE CAŁĄ TWOJĄ UFS!!!! OZNACZA TO, ŻE TWOJE URZĄDZENIE ZOSTANIE TRWAŁE USZKODZONE BEZ ROZWIĄZANIA! (z wyjątkiem zabrania urządzenia do Xiaomi lub flashowania go za pomocą EDL, co prawdopodobnie będzie kosztować)
```cmd
diskpart
```

#### Znajdowanie telefonu
> Spowoduje to wyświetlenie listy wszystkich podłączonych dysków
```cmd
lis dis
```

#### Wybieranie telefonu
> Zastąp $ rzeczywistym numerem partycji telefonu (powinien być ostatnim)
```cmd
sel dis $
```

#### Lista partycji Twojego telefonu
> Spowoduje to wyświetlenie listy partycji urządzenia
```cmd
lis par
```

#### Wybór partycji Windows
> Zastąp $ numerem partycji systemu Windows (powinno być 23)
```cmd
sel par $
```

#### Formatowanie dysku z systemem Windows
```cmd
format quick fs=ntfs label="WIN8PRO"
```

#### Dodaj literę do systemu Windows
```cmd
assign letter x
```

#### Wybieranie Partycji ESP
> Zamień $ na numer partycji ESP (powinno być 22)
```cmd
sel par $
```

#### Formatowanie ESP
```cmd
format quick fs=fat32 label="ESP8PRO"
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
 
> Jeśli poprosi Cię o podanie litery, wpisz literę dysku **WIN8PRO** (która powinna być X), a następnie naciśnij enter.

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

#### Wybierz głośność systemu Windows w telefonie
> Użyj `list Volume`, aby go znaleźć, zamień „$” na rzeczywistą liczbę **WIN8PRO**
```część dysku
sel vol $
```

#### Usuń przypisanie litery X
```część dysku
remove letter x
```

#### Wybierz głośność systemu ESP w telefonie
> Użyj `list Volume`, aby go znaleźć, zamień „$” na rzeczywistą liczbę **ESP8PRO**
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

### Naprawianie dotyku
> Uruchom ponownie telefon w trybie fastboot, a następnie zamień **path\to** rzeczywistą ścieżką do obrazu devcfg (który pobrałeś wczesniej)
```cmd
fastboot flash devcfg_ab path\to\devcgf-equuleus.img
```

### Uruchom ponownie do Androida
> Uruchom ponownie do Androida aby ustawić dualboot


## [Ostatni Krok: Ustawianie dualboot](dualboot.md)

















