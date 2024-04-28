<img align="right" src="https://github.com/n00b69/woa-equuleus/blob/main/equuleus.png" width="350" alt="Windows 11 running on equuleus">

# Windows na Xiaomi Mi 8 Pro

## Aktualizowanie sterowników

### Wymagania
- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Sterowniki](https://github.com/n00b69/woa-equuleus/releases/tag/Drivers)

- [Skrypt Msc](https://github.com/n00b69/woa-equuleus/releases/download/Files/msc.sh)
  
- [TWRP](https://github.com/n00b69/woa-equuleus/releases/download/Files/twrp.img) (powinno już być zainstalowane)

#### Uruchom do TWRP
> Jeśli Xiaomi zastąpiło Twoje recovery z powrotem do stanu magazynowego, sflashuj je ponownie w trybie fastboot za pomocą:
```cmd
fastboot flash recovery path\to\twrp.img
```

#### Uruchamianie skryptu msc
> Umieść msc.sh w folderze platform-tools, a następnie uruchom:
```cmd
adb push msc.sh / && adb shell sh msc.sh
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
 
> Jeśli poprosi Cię o podanie litery, wpisz literę dysku **WIN8PRO** (która powinna być X), a następnie naciśnij enter.

### Usuń przypisanie litery dysku
> Żeby nie pozostał tam po odłączeniu urządzenia
```cmd
część dysku
```

#### Wybierz głośność systemu Windows w telefonie
> Użyj `list Volume`, aby go znaleźć, zamień „$” na rzeczywistą liczbę **WIN8PRO**
```część dysku
wybierz głośność $
```

#### Usuń przypisanie litery X
```część dysku
usuń literę x
```

#### Wyjdź z dysku
```część dysku
Wyjście
```

#### Uruchom ponownie system Windows
> Uruchom ponownie urządzenie, aby ponownie uruchomić system Windows. Jeśli spowoduje to uruchomienie systemu Android, ponownie wykonaj flashowanie obrazu UEFI poprzez fastboot lub za pomocą aplikacji WOA Helper


## Skończone!















