<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Aktualizowanie sterowników

### Wymagania
- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Sterowniki](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)

- [obraz UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

### Uruchom do UEFI
> Zastąp **<path\to\beryllium-uefi.img>** rzeczywistą ścieżką obrazu UEFI
```cmd
fastboot boot <path\to\beryllium-uefi.img>
```

### Diskpart
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

#### Dodaj literę do systemu Windows
```cmd
assign letter x
```

#### Wyjdź z Diskpart
```cmd
exit
```

### Instalowanie sterowników
> Wypakuj archiwum ze sterownikami, potem otwórz plik `OfflineUpdater.cmd`
 
> Jeśli poprosi Cię o podanie litery, wpisz literę dysku **WINF1** (która powinna być X), a następnie naciśnij enter.

### Uruchom ponownie system Windows
> Uruchom ponownie urządzenie, aby ponownie uruchomić system Windows. Jeśli spowoduje to uruchomienie systemu Android, ponownie wykonaj flashowanie obrazu UEFI poprzez fastboot lub za pomocą aplikacji WOA Helper


## Skończone!















