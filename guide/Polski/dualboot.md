<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Dualboot

### Wymagania
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [Obraz UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

- [WOA Helper](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)

## Przewodnik Dualboot
W tym przewodniku założono, że jesteś zrootowany, jeśli tak nie jest, postępuj zgodnie z [tym przewodnikiem](root.md)

### Konfiguracja – Android
- Pobierz i zainstaluj aplikację **WOA Helper**, a następnie otwórz ją i przyznaj uprawnienia root.
- Pobierz **obraz UEFI** i umieść go w folderze o nazwie „UEFI” w pamięci wewnętrznej.
- Otwórz aplikację WOA Helper i użyj **STA CREATOR** w **WOA TOOLBOX**.
> [!Important]
> Jeśli `/sdcard/Windows` jest pusty, Twój ROM nie obsługuje montowania i będziesz musiał wykonać kopię zapasową boot.img w aplikacji, a następnie skopiować ją ręcznie do systemu Windows po uruchomieniu (na przykład przesyłając go gdzieś a następnie pobranie go podczas uruchamiania systemu Windows). To samo dotyczy plików StA, które są również generowane w pamięci wewnętrznej.
>
> Zrób to samo, jeśli folder jest tylko do odczytu.
- Naciśnij przycisk **SZYBKIE URUCHAMIANIE DO WINDOWS**.

### Konfiguracja — Windows
> [!Tip]
> If this is your first time booting Windows and you wish to skip the Microsoft Account login, press the **I don't have internet** button in the WiFi page, then when prompted, press the **Continue with limited setup** button.
- Navigate to `C:\sta` and create a shortcut of **sta.exe** to your desktop, if one isn't already present

#### Uruchamianie systemu Android
- Uruchom nowy skrót na pulpicie (możesz także przypiąć go do menu startowego/paska zadań, aby ułatwić dostęp)

#### Uruchamianie systemu Windows
- Naciśnij „Quickboot to Windows” w aplikacji lub użyj nowo utworzonego przełącznika w panelu szybkich ustawień
  
## Skończone!









