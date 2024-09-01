<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Przywracanie urządzenia za pomocą trybu EDL

### Wymagania
- [Oryginalny ROM fastboot](https://xmfirmwareupdater.com/miui/beryllium/)

- [Narzędzia EDL](https://github.com/n00b69/woa-beryllium/releases/download/Files/Xiaomi845freeEDL.zip)

### Wydobywanie oryginalnego ROM-u
> Pobierz oryginalny ROM fastboot dla swojego urządzenia (który powinien być w formacie .tgz), a następnie wyodrębnij zawartość pliku .tar znajdującego się wewnątrz

### Uruchamianie w tryb EDL
> Jeśli jesteś już w EDL, możesz pominąć ten krok
- Pobierz i rozpakuj **Xiaomi845freeEDL.zip**. Może być konieczne wyłączenie oprogramowania antywirusowego lub może ono zostać błędnie wykryte jako złośliwe oprogramowanie.
- W trybie fastboot otwórz **XiaomiFree9008ForQ845.exe**.
- Naciśnij **2**, a następnie potwierdź, naciskając **enter**, aby uruchomić telefon w trybie EDL.

#### Znalezienie numeru COM##
> Oprogramowanie powinno otworzyć menedżer urządzeń. Jeśli tak się nie stanie, otwórz go ręcznie
- Znajdź urządzenie o nazwie **Qualcomm HS-USB QDLoader 9008 (COM##)** w sekcji **Porty (COM i LPT)**.
> [!Important]
> Jeśli urządzenie ma ⚠️ żółty trójkąt ostrzegawczy, musisz zainstalować sterowniki EDL, zanim będziesz mógł przejść do następnego kroku
- Zapisz numer **COM##** na końcu **Qualcomm HS-USB QDLoader 9008 (COM##)**.
- W menu naciśnij **1**, a następnie **enter**. Następnie zapyta o port komunikacyjny: wprowadź numer **COM##**, a następnie naciśnij **enter**

### Flashowanie stockowego romu
- Skopiuj i wklej pełną ścieżkę do folderu obrazów w wyodrębnionym ROMie Fastboot z pierwszego kroku, a następnie naciśnij **Enter**, aby rozpocząć flashowanie ROMu.
> Powinno wyglądać mniej więcej tak: `C:\Users\alak_romanian\Downloads\polaris_global_images_V12.0.3.0.QDGMIXM_20201228.0000.00_10.0_global\images`

#### Uruchom ponownie system Android
> Po zakończeniu flashowania pamięci ROM (może to zająć około 5 minut) po prostu uruchom ponownie urządzenie, aby ponownie uruchomić system Android

## Skończone!










