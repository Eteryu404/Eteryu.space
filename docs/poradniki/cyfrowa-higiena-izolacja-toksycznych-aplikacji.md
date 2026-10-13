---
title: "Jak odizolować toksyczne aplikacje na Androidzie"
description: "Dwie warstwy obrony przed aplikacjami, które szpiegują: RethinkDNS jako firewall i szyfrowany DNS, oraz systemowa izolacja przez Private Space albo osobny profil użytkownika."
icon: lucide/box
---

Niektóre aplikacje są potrzebne do życia lub pracy, ale ich kod pisali specjaliści od wysysania danych. Microsoft Teams, Facebook, Messenger, aplikacje linii lotniczych, dyskontów spożywczych. Potrafią żądać dostępu do kontaktów i całej galerii, a jeśli im odmówisz, bywają upierdliwe albo wręcz odmawiają działania.

Ten poradnik pokazuje dwie warstwy obrony: kontrolę nad tym, co aplikacje wysyłają do sieci, oraz izolację, która odcina je od Twoich prawdziwych danych.

## 1. RethinkDNS jako sieciowy scyzoryk

Fabryczny Android ma jedną wadę architektoniczną: pozwala na uruchomienie tylko **jednego tunelu VPN na raz**. Chcesz zablokować aplikacji dostęp do sieci przez firewall? System stawia lokalny VPN. Chcesz zaszyfrować ruch przez Mullvada? Włączenie kolejnego VPN natychmiast wyłącza ten pierwszy. Efekt: albo chronisz prywatność w drodze do serwera, albo kontrolujesz, co ucieka z telefonu.

`RethinkDNS` rozwiązuje ten problem. Działa jak centralny hub, który bierze na siebie całą komunikację sieciową telefonu, ale wewnątrz pozwala skonfigurować trzy niezależne warstwy. Dopiero gdy wszystko ustawisz, aplikacja odpala jeden lekki tunel systemowy.

### Warstwa pierwsza: DNS

W zakładce `DNS` nie musisz polegać na domyślnych serwerach operatora. Możesz wybrać wbudowane w Rethinka listy blokujące albo podpiąć zewnętrzny adres, np. `9.9.9.9` od `Quad9` czy własny profil `NextDNS`. Każde zapytanie o domenę reklamową zostanie ubite na starcie.

### Warstwa druga: Firewall

W zakładce `Apps` możesz włączyć tryb `Whitelisting`, który domyślnie blokuje wszystko oprócz wybranych aplikacji. Możesz też przejrzeć listę i odciąć internet kalkulatorowi, czytnikowi PDF czy gierce offline.

### Warstwa trzecia: Proxy i VPN

W sekcji `Proxy` wybierasz `WireGuard` i importujesz zwykły plik konfiguracyjny `.conf`, który pobierasz ze strony swojego dostawcy VPN (Mullvad, Proton). Nie musisz instalować osobnej aplikacji.

### Jak to działa razem

Klikasz start w RethinkDNS. System tworzy jeden tunel. Od tej chwili:

1. Toksyczna aplikacja próbuje wysłać paczkę danych.
2. Firewall sprawdza, czy ma na to zgodę.
3. Jeśli tak, DNS filtruje, czy adres nie jest trackerem.
4. Czysty ruch zostaje zapakowany w tunel WireGuard i wysłany w świat.

Wszystko dzieje się w ułamku sekundy, w jednym procesie, bez kłótni systemowych i bez katowania baterii kilkoma aplikacjami w tle.

## 2. Cyfrowa kwarantanna dla toksycznych aplikacji

Aplikacje, których potrzebujesz, ale którym nie ufasz, możesz zamknąć w piaskownicy. Android ma do tego dwa mechanizmy.

=== "Private Space / Secure Folder (wewnątrz profilu)"

    Jeśli masz nowszego Androida z funkcją `Private Space` lub telefon Samsung z `Bezpiecznym Folderem`, konfiguracja jest prosta.

    1. Wejdź w ustawienia bezpieczeństwa systemu.
    2. Aktywuj osobną przestrzeń i zabezpiecz ją osobnym PIN-em lub odciskiem palca.
    3. Na dole listy aplikacji pojawi się zablokowana sekcja.

    Aplikacje instalujesz bezpośrednio wewnątrz tej przestrzeni. System odpala dla nich kompletnie czyste środowisko: mają osobną pamięć podręczną i nie widzą Twoich prywatnych zdjęć ani kontaktów z głównego profilu.

    Jeśli komunikator wewnątrz prywatnej przestrzeni zażąda dostępu do książki adresowej, możesz mu dać zgodę bez obaw. Aplikacja przeszuka bazę, zobaczy cyfrowe nic, nie zgłosi błędu. Myśli, że dostała to, czego chciała, a w rzeczywistości została oszukana.

    Na Samsungu powiadomienia zobaczysz na głównym ekranie w dyskretnej formie. Na czystym Androidzie z funkcją Private Space aplikacje zostaną całkowicie zamrożone i nie będą zużywać baterii, dopóki sam nie odblokujesz przestrzeni.

=== "Osobny profil użytkownika (pełna separacja)"

    Jeśli Twój telefon nie ma funkcji `Private Space`, możesz użyć klasycznych profili użytkowników.

    1. Wejdź w ustawienia systemowe.
    2. Wybierz `Użytkownicy` → `Dodaj użytkownika`.
    3. Przełącz się na nowy profil i zainstaluj tam aplikacje.

    System tworzy drugi, fabrycznie nowy telefon wewnątrz starego. Ta metoda daje najbardziej bezwzględną izolację, bo aplikacje z drugiego profilu są całkowicie zamrożone i nie mają żadnego kontaktu z głównym kontem.

    Haczyk: dopóki nie przełączysz się ręcznie na ten profil, nie zobaczysz powiadomień. To dobre rozwiązanie na aplikacje służbowe, które chcesz wyciszyć po godzinach pracy.

Niezależnie od wybranej metody efekt jest ten sam: toksyczna aplikacja ląduje w kontrolowanej piaskownicy, a Ty odzyskujesz prywatność bez rezygnacji z narzędzi potrzebnych do codziennego funkcjonowania.

## Podsumowanie

Łącząc `RethinkDNS` z systemową izolacją (`Private Space` lub profilami użytkowników), tworzysz wokół swoich danych mur o dwóch niezależnych warstwach. Pierwsza pilnuje, żeby z urządzenia nie wypłynął żaden nieautoryzowany pakiet. Druga dba o to, żeby aplikacje, na które jesteś skazany, żyły w cyfrowej niewiedzy.

Wszystkie te opcje masz już pod maską Androida. Wystarczy zacząć z nich korzystać.
