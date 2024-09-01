<img align="right" src="https://github.com/n00b69/woa-beryllium/blob/main/beryllium.png" width="350" alt="Windows 11 running on beryllium">

# Windows na Xiaomi Pocophone F1

## Konfiguracja dualboot

### Wymagania
- [Obraz UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)

- [WOA Helper](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)

## Przewodnik Dualboot
W tym przewodniku założono, że posiadasz roota, a jeśli tak nie jest, postępuj zgodnie z [tym przewodnikiem](root.md)

### Konfiguracja – Android
- Pobierz i zainstaluj aplikację **WOA Helper**, a następnie otwórz ją i przyznaj uprawnienia roota.
- Pobierz **obraz UEFI** i umieść go w folderze o nazwie `UEFI` w pamięci wewnętrznej.
- Otwórz aplikację WOA Helper app i naciśnij przycisk **SZYBKI START DO WINDOWS**.

### Konfiguracja — Windows
> [!Tip]
> Jeśli to będzie pierwszy raz, gdy uruchamiasz Windowsa i chcesz pominąć logowanie do konta Microsoft, wciśnij przycisk **Nie mam Internetu** w etapie WiFi, a gdy zapytany, wciśnij **Kontynuuj z ograniczoną konfiguracją**.

#### Uruchamianie systemu Android
- Uruchom nowy skrót na pulpicie (możesz także przypiąć go do menu startowego/paska zadań, aby mieć łatwiejszy dostęp)

#### Uruchamianie systemu Windows
- Naciśnij **SZYBKI START DO WINDOWS** w aplikacji lub użyj nowego przełącznika w panelu szybkich ustawień

> [!Important]
> If you ever update or change your Android ROM, make sure to create a new **boot.img** backup (after rooting your phone!) and place it inside the **C:\ folder** in Windows, overwriting the old file.
>
> You can use the **BACK UP BOOT IMAGE** feature in the WOA Helper app to do so.

## Skończone!
