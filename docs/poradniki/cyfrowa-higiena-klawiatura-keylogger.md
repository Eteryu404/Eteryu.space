---
title: "Jak zabezpieczyć klawiaturę i schowek na Androidzie"
description: "Domyślne klawiatury i schowek systemowy to dwa najczęściej ignorowane wektory wycieku danych. Poradnik pokazuje, jak je okiełznać i odciąć od sieci."
icon: lucide/keyboard
---

Kiedy myślimy o prywatności w smartfonie, instynktownie zaklejamy kamerę, blokujemy dostęp do mikrofonu i wyłączamy lokalizację. Tymczasem dobrowolnie oddajemy wszystkie nasze najskrytsze myśli, wpisywane hasła, numery kart i zapytania w wyszukiwarce jednemu niepozornemu elementowi systemu: klawiaturze ekranowej. Drugim jest schowek systemowy.

Ten poradnik pokazuje, jak zabezpieczyć oba te komponenty w duchu zero trust.

## Klawiatura jako keylogger

Domyślne klawiatury dostarczane ze współczesnymi systemami, z `Google Gboard` na czele, to zaawansowane koszmary telemetryczne. Pod przykrywką autokorekty, podpowiedzi słów i naklejek, nieustannie mapują Twój styl pisania i nawyki językowe.

Zbierają nie tylko słowniki Twoich prywatnych fraz, ale budują całe profile behawioralne na podstawie dynamiki uderzeń w klawisze. Mierzą tempo pisania, długość przerw, specyfikę popełnianych błędów. Lokalne słowniki automatyczne potrafią zapamiętywać i po czasie podpowiadać poufne dane, takie jak numery PIN, frazy z menedżera haseł czy dolegliwości wpisywane w oknie wyszukiwarki.

```text
[ ZAGROŻENIE: Telemetryczna klawiatura domyślna ]

 Uderzenie w klawisz ──► [ KLAWIATURA (np. Gboard) ] ──► [ Słownik lokalny / AI ]
                                   │
                                   ▼ (Telemetria i statystyki)
                       [ SERWERY GOOGLE / CLOUD ]


[ ROZWIĄZANIE: Odizolowana maszyna do pisania ]

 Uderzenie w klawisz ──► [ HELIBOARD / FUTO ] ──► System Android (AOSP)
                                   │
                                ( X ) ──► BRAK INTERNETU / ZABLOKOWANY FIREWALL
```

### iOS: metoda prymitywnej maszyny do pisania

W zamkniętym ekosystemie Apple instalowanie zewnętrznych klawiatur bywa problematyczne pod kątem uprawnień. Producent chwali się prywatnością różnicową i przetwarzaniem danych głównie na urządzeniu, jednak w myśl zasady ograniczonego zaufania nie chcesz, żeby system tworzył jakiekolwiek słowniki Twoich zachowań.

Najskuteczniejszą metodą jest ograniczenie funkcji klawiatury systemowej. Wejdź w ustawienia ogólne → klawiatury i wyłącz:

- Autokorektę,
- Sprawdzanie pisowni,
- Podpowiedzi tekstowe,
- Automatyczne wielkie litery.

Klawiatura zostaje sprowadzona do roli maszyny do pisania. Jej zadaniem jest wprowadzanie znaków bez semantycznej analizy tekstu, bez próby zgadywania Twoich intencji i bez budowania lokalnego indeksu haseł.

### Android: bezpieczne alternatywy i odcięcie od sieci

Android daje pełną wolność i pozwala na całkowite usunięcie klawiatury producenta. Najlepsze alternatywy zorientowane na prywatność to `HeliBoard` oraz `FUTO Keyboard`.

Co sprawia, że są bezpieczne:

- **Przejrzystość kodu.** `HeliBoard` to projekt FOSS. `FUTO Keyboard` nie ma ścisłej licencji FOSS, ale udostępnia kod do wglądu i działa wyłącznie offline.
- **Brak uprawnienia do sieci.** `HeliBoard` na poziomie manifestu nie deklaruje dostępu do internetu (`android.permission.INTERNET`). Fizycznie nie ma w kodzie funkcji pozwalającej na połączenie z siecią. `FUTO` stosuje podobną filozofię.
- **Awaryjna zapora sieciowa.** Jeśli musisz korzystać ze standardowej klawiatury, użyj `RethinkDNS` i zablokuj jej ruch sieciowy na poziomie pakietowym.
- **Wyłączone uczenie i lokalne słowniki.** Nawet jeśli klawiatura jest odcięta od sieci, w ustawieniach wyłącz opcje uczenia się wpisywanego tekstu. Lokalny słownik z hasłami może zostać mimowolnie wysłany przez systemową kopię zapasową. Nadgorliwe podpowiedzi mogą też zdradzić hasło osobie zerkającej przez ramię (shoulder surfing), a złośliwe aplikacje z uprawnieniami ułatwień dostępu (Accessibility Services) mogą odczytać podpowiadane frazy z ekranu.

## Schowek: otwarta księga

Schowek to tymczasowy bufor pamięci RAM, do którego trafia wszystko, co skopiujesz. Kody jednorazowe z SMS, hasła i tokeny z menedżera haseł, numery kont bankowych, adresy portfeli kryptowalutowych.

Do niedawna schowek był strefą całkowicie niechronioną. Dopiero iOS 14 i Android 12 zaczęły wyświetlać alerty o odczycie schowka. Nagle okazało się, że dziesiątki popularnych aplikacji pasywnie skanowały zawartość bufora przy każdym uruchomieniu lub wpisaniu znaku.

### Ataki typu Clipper

`Clipper` to złośliwe oprogramowanie, które monitoruje zawartość schowka w poszukiwaniu wzorców przypominających numery kont lub adresy kryptowalutowe. Kiedy wykryje skopiowany ciąg, w ułamku sekundy podmienia go w pamięci na adres należący do atakującego. Jeśli wkleisz adres i klikniesz wyślij, środki znikną bezpowrotnie.

```text
[ ATAK TYPU CLIPPER: Podmiana bufora ]

Skopiowano:  PL 12 3456 7890 ... (Twój bank)
                    │
                    ▼
          [ ZŁOŚLIWY CLIPPER ] ──► Podmienia bufor w RAM
                    │
Wklejono:    PL 99 8765 4321 ... (Konto Hakera)


[ BEZPIECZNY SCHOWEK: Czyszczenie i izolacja ]

Menedżer haseł ──► [ SCHOWEK RAM ] ──► ( Wklejenie hasła )
                        │
                  [ TIMER 20s ] ──► ( BUFOR AUTOMATYCZNIE WYCZYSZCZONY! )
```

### Cztery filary bezpiecznego schowka

**1. Wyłącz historię schowka w klawiaturze.** Funkcje takie jak historia schowka w Gboardzie tworzą niezaszyfrowany rejestr wszystkiego, co zostało skopiowane w ciągu dnia. W ustawieniach klawiatury wyłącz przechowywanie historii skopiowanych elementów.

**2. Ustaw automatyczne czyszczenie bufora.** Android 13 czyści schowek systemowy po 60 minutach, ale dla haseł to wciąż ogromne okno ekspozycji. Menedżery haseł takie jak `Bitwarden` czy `KeePassDX` mają funkcję wyczyszczenia schowka po kilkudziesięciu sekundach. Upewnij się, że jest aktywna.

**3. Restrykcyjna kontrola uprawnień.** W nowszych wersjach systemów (iOS, Android) oraz w wariantach ukierunkowanych na utwardzenie, takich jak `GrapheneOS`, zwracaj uwagę na powiadomienia (toast notifications) o tym, że aplikacja uzyskała dostęp do schowka. Jeśli usługa lub gra pyta o dostęp, odrzuć prośbę lub odbierz uprawnienie w ustawieniach.

**4. Weryfikacja kontekstowa.** Nawet na utwardzonym telefonie wypracuj nawyk precyzyjnego sprawdzania danych. Przy przelewach bankowych i przesyłaniu krytycznych danych weryfikuj pierwsze i ostatnie znaki wklejonego ciągu. To najprostsza tarcza na ataki typu Clipper.

## Podsumowanie

Wygoda to największy wróg bezpieczeństwa. Inteligentne autokorekty, uczące się słowniki i zapamiętywanie skopiowanych haseł brzmią jak ułatwienie, ale generują ogromną powierzchnię ataku.

Wyciszając klawiaturę do poziomu prostej maszyny do pisania, odcinając jej dostęp do sieci i wymuszając automatyczne czyszczenie schowka, odzyskujesz kontrolę nad najważniejszym punktem styku z urządzeniem. Cyfrowy sejf na nic się nie zda, jeśli klawiatura sama raportuje na zewnątrz każdą kombinację cyfr, którą wprowadzasz.
