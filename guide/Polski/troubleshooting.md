<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Rozwiązywanie problemów
> Poniżej znajdziesz listę typowych problemów i ich rozwiązań

## LTE i inne usługi sieciowe w Androidzie już nie działają
> Czasami system Windows może wyczyścić partycje modemu, powodując utratę LTE w systemie Android. Aby to naprawić, musisz przywrócić modem, korzystając z kopii zapasowych, które, miejmy nadzieję, wykonałeś [podczas partycjonowania urządzenia](1-partition.md#backing-up-important-files). Jeśli nie wykonałeś tego kroku, prawdopodobnie nie będzie możliwości odzyskania danych.
- Uruchom dowolne odzyskiwanie inne niż odzyskiwanie zapasów (polecenia ADB tam nie działają)
- Otwórz CMD w folderze **narzędzia platformy**.
- Przywróć cztery partycje, których kopię zapasową utworzono, używając poniższych poleceń. Zastąp `path\to` rzeczywistą ścieżką obrazów.
```cmd
adb push path\to\fsc.bin /cache/ & adb shell dd if=/cache/fsc.bin of=/dev/block/by-name/fsc
```

```cmd
adb push path\to\fsg.bin /cache/ & adb shell dd if=/cache/fsg.bin of=/dev/block/by-name/fsg
```

```cmd
adb push path\to\modemst1.bin /cache/ & adb shell dd if=/cache/modemst1.bin of=/dev/block/by-name/modemst1
```

```cmd
adb push path\to\modemst2.bin /cache/ & adb shell dd if=/cache/modemst2.bin of=/dev/block/by-name/modemst2
```
- Uruchom ponownie urządzenie i sprawdź, czy działa LTE.
> [!Note]
> Jeśli to nadal nie zadziała, będziesz musiał wykonać kilka dodatkowych kroków;
- Pobierz [wersję ROM dla swojego urządzenia](https://xmfirmwareupdater.com/miui/beryllium/)
- Otwórz go, poszukaj pliku o nazwie **modem.img** i rozpakuj go.
- Uruchom system w trybie fastboot (`adb restart bootloader`.
- Wgraj plik **modem.img** poniższym poleceniem, zastępując `ścieżkę\do\modem.img` rzeczywistą ścieżką obrazu
```cmd
fastboot flash modem path\to\modem.img
```

##### Skończone!

## LTE in Windows does not work
> [!Note]
> You may have to follow the steps above to restore your modem first
- In Android, find your APN settings. It should be located in `Connections` > `Mobile Networks` > `Access Point Names`.
- Write the information of your current APN settings down, then boot into Windows.
- In `Cellular Settings`, click on `Mobile operator settings` > `APN settings` and add the APN settings you wrote down earlier.
- Enable **Cellular**. It may say `No Internet Access`, but it should still work. 

##### Finished!

## Device is not recognized in fastboot or recovery
> This likely means you don't have (proper) USB drivers installed
- Download [QUD.zip](https://github.com/n00b69/woa-betalm/releases/download/Qfil/QUD.zip) here and extract it.
- Open Device Manager and find an unknown device or device with errors that may be called **Android**, **ADB Interface**, or **QUSB_BULK**.
- Right click this devjce, select "Update Drivers" > "Browse files", then select the **QUD folder** you extracted before.

##### Finished!

## Nie można zamontować systemu Windows w systemie Android
> Dzieje się tak, gdy zamykasz system Windows zamiast go ponownie uruchamiać.
- Aby rozwiązać ten problem, uruchom system Windows, a następnie naciśnij „Uruchom ponownie”, a następnie, gdy ekran się wyłączy, uruchom system TWRP i stamtąd załaduj system Android.
> Alternatywnie, jeśli masz już skonfigurowaną aplikację Przełącz na Androida, po prostu użyj jej, aby przejść na Androida.

##### Skończone!

## USB nie działa
Włącz tryb hosta USB, korzystając z [przewodnika dotyczącego przełączania trybu hosta USB](materials.md#przełączanie-trybu-hosta-usb).

##### Skończone!

## Błąd DISM: 87 Opcja dodawania sterownika jest nieznana
Zwykle oznacza to, że masz nieczysty obraz systemu Windows z innymi sterownikami. Musisz uzyskać czysty obraz systemu Windows (co oznacza, że ​​nie postępowałeś zgodnie z instrukcjami).

##### Skończone!

## BSOD 0xc000021a
Zwykle oznacza to, że plik winlogon.exe nie powiódł się i może być konieczne ponowne zastosowanie obrazu systemu Windows.

##### Skończone!

## Komputer nieoczekiwanie uruchomił się ponownie lub napotkał nieoczekiwany błąd
Jeśli natkniesz się na ten błąd, może być konieczne ponowne wdrożenie obrazu systemu Windows. Skorzystaj w tym celu z [przewodnika ponownej instalacji](2-install.md).

##### Skończone!

## INACCESSIBLE_BOOT_DEVICE BSOD
Ten niebieski ekran śmierci prawdopodobnie oznacza uszkodzoną instalację sterownika. Aby rozwiązać ten problem, zainstaluj ponownie sterowniki, korzystając z [przewodnika ponownej instalacji](2-install.md).

##### Skończone!



















