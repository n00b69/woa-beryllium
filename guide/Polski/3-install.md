<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Instalacja Windowsa

### Wymagania
- [Zmodyfikowane recovery OFOX](https://github.com/n00b69/woa-beryllium/releases/tag/Recovery)

- [Windows na ARM](https://arkt-7.github.io/woawin/)
  
- [Sterowniki](https://github.com/n00b69/woa-beryllium/releases/tag/Drivers)

- [Obraz UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

### Uruchomienie recovery OFOX
> Jeśli recovery zostało zastąpione recovery domyślnym, sflashuj go ponownie za pomocą
```cmd
fastboot flash recovery ścieżka\do\ofox-beryllium.img reboot recovery
```

#### Włączanie trybu pamięci masowej
> Jeżeli zostałeś poproszony, aby wykonać polecenie jeszcze raz, zrób to
```cmd
adb shell msc
```

### Diskpart
> [!WARNING]
> NIE USUWAJ ŻADNYCH PARTYCJI W DISKPART!!!! TO USUNIE CAŁĄ ZAWARTOŚĆ PAMIĘCI!!!! OZNACZA TO, ŻE TWOJE URZĄDZENIE ZOSTANIE TRWALE USZKODZONE BEZ ROZWIĄZANIA! (z wyjątkiem wysłania go do Xiaomi lub flashowania go za pomocą [EDL](edl.md))
```cmd
diskpart
```

#### Wybieranie partycji Windows
> Wpisz `list Volume`, aby ją znaleźć, zamień `$` na rzeczywistą liczbę **WINF1**
```diskpart
select volume $
```

#### Dodanie litery do systemu Windows
```cmd
assign letter x
```

#### Wybieranie partycji ESP
> Użyj `list Volume`, aby go znaleźć, zamień `$` na rzeczywistą liczbę **ESPF1**
```diskpart
select volume $
```

#### Dodanie literę do ESP
```cmd
assign letter y
```

#### Wyjście z Diskpart
```cmd
exit
```

### Instalowanie Windowsa
> [!WARNING]
> NIE UŻYWAJ 24H2!!!

> Zamień `ścieżka\do\install.esd` na rzeczywistą ścieżkę do pliku install.esd (może on również nosić nazwę install.wim lub 22631.2861.XXXXXXX.esd)
```cmd
dism /apply-image /ImageFile:ścieżka\do\install.esd /index:6 /ApplyDir:X:\
```

> Jeśli pojawi się komunikat `Błąd 87`, sprawdź indeks obrazu za pomocą polecenia `dism /get-imageinfo /ImageFile:ścieżka\do\install.esd`, a następnie zastąp `index:6` rzeczywistym numerem indeksu systemu **Windows 11 Pro** w Twoim obrazie

### Kopiowanie obrazu rozruchu do Windowsa
- Zaznacz i upuść **rooted_boot.img** z poprzedniego kroku do **WINF1** w eksploratorze plików, a następnie zmień mu nazwę na **boot.img**.

### Instalowanie sterowników
- Wypakuj archiwum ze sterownikami, a następnie otwórz plik `OfflineUpdater.cmd` (jeśli pojawi się błąd, otwórz `OfflineUpdaterFix.cmd`)
 
> Jeśli poprosi Cię o podanie litery, wpisz literę dysku **WINF1** (która powinna być **X**), a następnie naciśnij enter.

#### Tworzenie plików bootloadera systemu Windows
> If any error shows up, such as "Failure when attempting to copy boot files", open `diskpart` again and assign any new letter to **ESPF1**, then replace the letter `Y` in the next commands with the letter that you just added.
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Włączanie trybu testowego
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

#### Remove the drive letter for ESP
> If this does not work, ignore it and skip to the next command. This phantom drive will disappear the next time you reboot your PC.
```cmd
mountvol y: /d
```

### Uruchamianie ponownie w trybie fastboot
```cmd
adb reboot bootloader
```

#### Booting firstboot.img
> Download **firstboot-paneltype.img** for your device's panel and replace **path\to** with the actual path to the image
>
> Reboot to recovery and use `adb shell panel` in the modified recovery if you forgot what panel you have

> [!Important]
> Remove your USB cable right after leaving the fastboot screen, or Windows may crash in the initial setup, which will then require a reinstall
```cmd
fastboot boot path\to\firstboot-paneltype.img
```

### Uruchamianie ponownie do Androida
Telefon powinien uruchomić się ponownie sam po +- 10 minutach czekania, po których uruchomi się Android, aby wykonać ostatni krok.

## [Ostatni krok: Konfiguracja dualboot](4-dualboot.md)

















