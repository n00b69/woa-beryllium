<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Aktualizowanie sterowników

### Wymagania
- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Zmodyfikowane recovery OFOX](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)
  
- [Sterowniki](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)

- [Obraz UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

### Uruchomienie recovery
> Jeśli recovery zostało zastąpione recovery domyślnym, sflashuj go ponownie za pomocą
```cmd
fastboot flash recovery ścieżka\do\ofox.img reboot recovery
```

#### Włączanie trybu pamięci masowej
> Jeżeli ci mówi aby wykonać polecenie jescze raz to zrób to
```cmd
adb shell msc
```

### Diskpart
```cmd
diskpart
```

#### Wybór partycji Windows
> Użyj `list Volume`, aby go znaleźć, zamień `$` na rzeczywistą liczbę **WINF1**
```diskpart
select volume $
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
> [!Note]
> Ten proces zajmie +- 20 minut. Nie martw się, to normalne.

- Wypakuj archiwum ze sterownikami, potem otwórz plik `OfflineUpdater.cmd` (jeśli pojawi się błąd, otwórz `OfflineUpdaterFix.cmd`)
 
> Jeśli poprosi cię o podanie litery, wpisz literę dysku **WINF1** (która powinna być **X**), a następnie naciśnij enter.

### Uruchom ponownie urządzenie
> Pamiętaj, aby zmienić także obraz UEFI w systemie Android, w przeciwnym razie podczas późniejszego uruchamiania systemu Windows może pojawić się „niebieski ekran śmierci” (BSoD).
```cmd
adb reboot
```

## Skończone!














