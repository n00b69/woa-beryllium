<img align="right" src="https://github.com/n00b69/woa-equuleus/blob/main/equuleus.png" width="350" alt="Windows 11 running on equuleus">

# Windows na Xiaomi Mi 8 Pro

## Dualboot

### Wymagania
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [Obraz UEFI](https://github.com/n00b69/woa-equuleus/releases/tag/UEFI)

- [WOA Helper](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)

- [StA](https://github.com/n00b69/woa-equuleus/releases/download/Files/equuleus-sta.zip)

## Przewodnik Dualboot
W tym przewodniku założono, że jesteś zrootowany, jeśli tak nie jest, postępuj zgodnie z [tym przewodnikiem](root.md)

### Konfiguracja – Android
- Pobierz i zainstaluj aplikację WOA Helper, a następnie otwórz ją i przyznaj uprawnienia roota.
- Pobierz obraz UEFI i umieść go w folderze o nazwie `UEFI` w pamięci wewnętrznej.
- Naciśnij przycisk `Zamontuj system Windows`, aby zamontować system Windows w pamięci wewnętrznej w `/sdcard/Windows`
> [!Important]
> Jeśli `/sdcard/Windows` jest pusty, Twój ROM nie obsługuje montowania i będziesz musiał wykonać kopię zapasową boot.img w aplikacji, a następnie skopiować ją ręcznie do systemu Windows po uruchomieniu (na przykład przesyłając go gdzieś a następnie pobranie go podczas uruchamiania systemu Windows). To samo dotyczy plików STA.
>
> Zrób to samo, jeśli folder jest tylko do odczytu.
- Utwórz folder o nazwie `sta` w systemie Windows i rozpakuj dwa pliki w pliku `Switch to Android` tutaj (pliki powinny trafić do `/sdcard/Windows/sta`
- Wróć do aplikacji WOA Helper i naciśnij przycisk `Quickboot`.

### Konfiguracja — Windows
- Przejdź do C:\sta i utwórz skrót `sta.exe` na pulpicie.

#### Uruchamianie systemu Android
- Uruchom nowy skrót na pulpicie (możesz także przypiąć go do menu startowego/paska zadań, aby ułatwić dostęp)

#### Uruchamianie systemu Windows
- Naciśnij „Quickboot to Windows” w aplikacji lub użyj nowo utworzonego przełącznika w panelu szybkich ustawień
  
## Skończone!




















