<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Konfiguracja dualboot

### Wymagania
- [Obraz UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

- [WOA Helper](https://github.com/n00b69/woa-helper/releases/tag/APK)

## Przewodnik Dualboot
W tym przewodniku założono, że jesteś zrootowany, jeśli tak nie jest, postępuj zgodnie z [tym przewodnikiem](root.md)

### Konfiguracja – Android
- Pobierz i zainstaluj aplikację **WOA Helper**, a następnie otwórz ją i przyznaj uprawnienia root.
- Pobierz **obraz UEFI** i umieść go w folderze o nazwie `UEFI` w pamięci wewnętrznej.
- Otwórz aplikację WOA Helper i użyj **STA CREATOR** w **WOA TOOLBOX**.
> [!Important]
> Jeśli `/sdcard/Windows` jest pusty, Twój ROM nie obsługuje montowania i będziesz musiał wykonać kopię zapasową boot.img w aplikacji, a następnie skopiować ją ręcznie do systemu Windows po uruchomieniu (na przykład przesyłając go gdzieś a następnie pobranie go podczas uruchamiania systemu Windows). To samo dotyczy plików StA, które są również generowane w pamięci wewnętrznej.
>
> Zrób to samo, jeśli folder jest tylko do odczytu.
- Naciśnij przycisk **SZYBKI START DO WINDOWS**.

### Konfiguracja — Windows
> [!Tip]
> Jeśli to będzie pierwszy raz, gdy uruchamiasz Windowsa i chcesz pominąć logowanie do konta Microsoft, wciśnij przycisk **Nie mam Internetu** w etapie WiFi, a gdy zapytany, wciśnij **Kontynuuj z ograniczoną konfiguracją**.
- Navigate to `C:\sta` and create a shortcut of **sta.exe** to your desktop, if one isn't already present

#### Uruchamianie systemu Android
- Uruchom nowy skrót na pulpicie (możesz także przypiąć go do menu startowego/paska zadań, aby ułatwić dostęp)

#### Uruchamianie systemu Windows
- Naciśnij **SZYBKI START DO WINDOWS** w aplikacji lub użyj nowo utworzonego przełącznika w panelu szybkich ustawień

> [!Important]
> Jeśli kiedykolwiek będziesz aktualizować lub zmieniać ROM, pamiętaj o utworzeniu nowej kopii zapasowej **boot.img** (po zrootowaniu telefonu!) i umieść ją w folderze C:\ w systemie Windows, zastępując stary plik.
>
> Możesz w tym celu skorzystać z funkcji **KOPIA OBRAZU ROZRUCHU** w aplikacji WOA Helper.

## Skończone!




























