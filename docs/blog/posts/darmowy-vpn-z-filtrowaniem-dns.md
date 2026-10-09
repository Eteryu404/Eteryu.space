---
title: "Darmowy VPN z filtrowaniem DNS. Proton VPN + DoH/DoT przez WG Tunnel"
description: "Jak połączyć darmowy Proton VPN z szyfrowanym DNS (DoH/DoT) i filtrowaniem reklam przez WG Tunnel. Standardowy WireGuard tego nie potrafi – zobacz, jak to obejść."
date: 2026-10-09
authors:
  - Eteryu
categories:
  - Prywatność
  - Narzędzia
---

Darmowy plan Proton VPN ma jedną poważną wadę. Nie ma w nim NetShield, czyli wbudowanego blokowania reklam, trackerów i malware. Płacący użytkownicy mają tę funkcję. Free tier dostaje tylko tunel.

To nie znaczy, że darmowy Proton jest bezużyteczny. Znaczy tylko, że trzeba mu trochę pomóc.

<!-- more -->

## Co oferuje darmowy Proton VPN

Zacznijmy od faktów. Darmowy plan Proton VPN to:

- **Brak limitu danych.** Nie ma throttlingu ani dziennego limitu transferu.
- **Jedno urządzenie.** Możesz połączyć tylko jeden telefon albo komputer naraz.
- **10 krajów.** Proton oferuje serwery w Holandii, Japonii, Rumunii, Polsce, USA, Meksyku, Kanadzie, Szwajcarii, Norwegii i Singapurze. Serwer jest przydzielany automatycznie, ale możesz przełączać się między krajami.
- **Brak NetShield.** Blokowanie reklam, trackerów i malware jest tylko w planach płatnych.
- **Brak custom DNS w natywnej aplikacji.** W oficjalnej aplikacji Proton VPN nie możesz ustawić własnego DNS. Ale jeśli korzystasz z pliku WireGuard `.conf`, możesz wpisać dowolny DNS w sekcji `[Interface]`. To ograniczenie dotyczy więc tylko aplikacji, nie protokołu.

Ostatnie dwa punkty bolą najbardziej. NetShield to funkcja, która filtruje zapytania DNS i blokuje domeny reklamowe oraz złośliwe. Custom DNS pozwala na wskazanie własnego resolvera, na przykład NextDNS albo HaGeZi DNS.

W płatnym planie możesz wybrać jedno albo drugie. Nie oba naraz. Proton traktuje je jako wzajemnie wykluczające się, bo NetShield sam filtruje DNS.

W darmowym nie masz żadnego z nich.

## Dlaczego nie wystarczy zwykły DNS w pliku .conf

Proton VPN udostępnia pliki konfiguracyjne WireGuard. Możesz je pobrać z panelu konta i zaimportować do dowolnego klienta WireGuard. W pliku `.conf` jest sekcja `[Interface]`, w której można wpisać adres DNS.

Więc tak, możesz dodać własny DNS już na tym etapie. Możesz tam wpisać adresy NextDNS, HaGeZi DNS albo dowolnego innego resolvera. I to zadziała.

!!! warning "Plain DNS w pliku .conf to nie to samo co szyfrowany DNS"

    Wpisanie adresu resolvera w sekcji `[Interface]` pliku `.conf` daje **plain DNS**. Zapytania lecą jako zwykły UDP na porcie 53, tylko wewnątrz tunelu WireGuard. Operator sieci ich nie widzi, ale Proton widzi. Po dotarciu do serwera Protona zapytanie jest odszyfrowywane i wysyłane dalej jako otwarty tekst. Jeśli chcesz szyfrowania end-to-end, potrzebujesz DoH albo DoT przez WG Tunnel.

Jeśli ufasz Protonowi, to nie problem. Proton ma politykę no-logs i niezależne audyty. Ale w modelu zero trust nie chodzi o to, komu ufasz. Chodzi o to, komu musisz ufać.

Wolę nie musieć ufać nikomu więcej niż to konieczne.

## Różnica między UDP a DoT i DoH

To jest sedno całego artykułu. Warto zrozumieć, dlaczego szyfrowany DNS jest lepszy od zwykłego, nawet jeśli ten zwykły jest w tunelu VPN.

| Protokół | Port | Szyfrowanie | Kto widzi zapytanie |
|---|---|---|---|
| **Plain DNS (UDP)** | 53 | Brak | Dostawca internetu, operator sieci, dostawca VPN |
| **DoT (DNS over TLS)** | 853 | Tak | Dostawca VPN (widzi zaszyfrowany ruch), ale nie treść |
| **DoH (DNS over HTTPS)** | 443 | Tak | Dostawca VPN (widzi ruch HTTPS), ale nie treść |

**Plain DNS** to zapytanie wysłane otwartym tekstem. Każdy na drodze może je odczytać i zmodyfikować. W tunelu VPN jest chroniony przed operatorem sieci, ale nie przed dostawcą VPN.

**DoT** to to samo zapytanie DNS, ale opakowane w TLS. Wygląda jak każdy inny zaszyfrowany ruch na porcie 853. Dostawca VPN widzi, że łączysz się z jakimś serwerem na tym porcie, ale nie widzi, o co pytasz.

**DoH** to zapytanie DNS opakowane w HTTPS. Wygląda jak zwykły ruch webowy na porcie 443. Dostawca VPN nie odróżni go od przeglądania strony. To najlepsza opcja pod kątem ukrycia zapytań DNS przed wszystkimi pośrednikami.

DoH i DoT dają więc coś, czego plain DNS nie daje: **szyfrowanie end-to-end między Twoim urządzeniem a resolverem DNS**. Nikt po drodze nie widzi treści zapytania. Ani operator sieci, ani Proton.

### Kiedy wybrać DoH, a kiedy DoT

Oba protokoły szyfrują DNS, ale różnią się charakterystyką. Wybór zależy od tego, gdzie i jak używasz telefonu.

**DoH — wybierz, jeśli:**

- Korzystasz z publicznych sieci Wi-Fi (kawiarnie, hotele, lotniska), które często blokują niestandardowe porty.
- Chcesz, żeby ruch DNS wyglądał jak zwykły ruch HTTPS. DoH używa portu 443, tego samego co przeglądanie stron. Trudniej go wykryć i zablokować.
- Zależy Ci na maksymalnym ukryciu zapytań DNS przed operatorem sieci.

**DoT — wybierz, jeśli:**

- Korzystasz głównie z sieci komórkowej albo domowego Wi-Fi, gdzie port 853 nie jest blokowany.
- Zależy Ci na niższych opóźnieniach. DoT jest „lżejszy" niż DoH, bo nie owija DNS w dodatkową warstwę HTTP.
- Administrujesz własnym serwerem DNS i chcesz używać standardowego portu dla DNS over TLS.

**Nie potrzebujesz ani DoH, ani DoT — jeśli:**

- Używasz VPN wyłącznie do ukrycia adresu IP i nie zależy Ci na ukryciu zapytań DNS przed dostawcą VPN.
- Ufasz Protonowi w kwestii nieprzetrzymywania logów DNS. Proton ma politykę no-logs i audyty, więc dla wielu użytkowników to wystarczy.

**Opcja pośrednia — Split DNS w WG Tunnel:**

Możesz też użyć trybu **Split** w WG Tunnel. W tym trybie tylko wybrane domeny (np. banki, usługi urzędowe) idą przez szyfrowany DNS, a reszta przez zwykły DNS systemowy. To kompromis między prywatnością a wydajnością.

## Rozwiązanie: WG Tunnel

Standardowy klient WireGuard na Androida nie obsługuje DoH ani DoT. Możesz wpisać adresy IP resolvera w pliku `.conf`, ale to wszystko. Nie ma opcji szyfrowania zapytań DNS.

**WG Tunnel** to alternatywny klient WireGuard, który obsługuje szyfrowany DNS bezpośrednio w aplikacji.

Ma cztery tryby pracy DNS:

- **Default** – używa domyślnych ustawień systemowych.
- **Encrypted** – wymusza szyfrowane zapytania (DoH lub DoT) przez cały tunel.
- **Split** – kieruje tylko wybrane domeny przez DNS tunelu, resztę przez system.
- **System VPN mode** – używa DNS dostarczonego przez Androida.

Dla naszego celu interesuje nas tryb **Encrypted**. W tym trybie WG Tunnel ignoruje adresy DNS z pliku `.conf` i używa własnego endpointu, który podajesz w ustawieniach aplikacji.

## Wybór resolvera DNS

Potrzebujesz resolvera, który obsługuje DoH albo DoT. Masz kilka opcji. Wybór zależy od tego, co chcesz blokować i ile kontroli potrzebujesz.

### Rekomendacja: Hagezi Pro + TIF

W społecznościach zajmujących się prywatnością i bezpieczeństwem sieciowym **Hagezi Pro + TIF** to obecnie złoty środek. HaGeZi to pseudonim niemieckiego dewelopera, który prowadzi jeden z najczęściej aktualizowanych i najlepiej ocenianych zestawów list blokujących na świecie.

**Hagezi Pro** to lista rozszerzona, która blokuje reklamy, trackery, analitykę, telemetrię, phishing, malware, scam i fake. Jest to wersja rekomendowana dla większości użytkowników.

**Hagezi TIF** (Threat Intelligence Feeds) to lista skupiona wyłącznie na zagrożeniach: phishing, malware, scam, fake i cryptojacking. Jest to poważne wzmocnienie bezpieczeństwa, rekomendowane jako uzupełnienie listy Pro.

Razem dają ochronę, która w testach blokowania osiąga wyniki powyżej 95%.

**Uwaga techniczna:** Lista Pro zawiera już część wpisów z TIF z ostatnich 14 dni, ale nie pełny feed. Pełny TIF jest szerszy i obejmuje zagrożenia starsze niż 14 dni. To wyjaśnia, dlaczego łączenie obu list ma sens.

### Darmowe resolvery oferujące Hagezi Pro + TIF bez rejestracji

Nie musisz mieć konta ani płacić, żeby korzystać z tych list. Kilka darmowych, non-profit resolverów oferuje gotowe presety z Hagezi Pro + TIF:

| Resolver | Adres DoH | Lokalizacja | Aktualizacje | Uwagi |
|---|---|---|---|---|
| **HaGeZi DNS (Falkenstein)** | `https://root.hagezi.org/dns-query` | Niemcy (Falkenstein) | Co 4-8h | Non-profit, EU |
| **HaGeZi DNS (Norymberga)** | `https://wurzn.hagezi.org/dns-query` | Niemcy (Norymberga) | Co 4-8h | Non-profit, EU |
| **HaGeZi DNS (Helsinki)** | `https://juuri.hagezi.org/dns-query` | Finlandia (Helsinki) | Co 4-8h | Non-profit, EU |
| **DNSWarden** | `https://dns.dnswarden.com/00000000000000000000018` | Nieokreślona | Nieokreślone | Pro + TIF |
| **DNSBUNKER.org** | `https://dnsbunker.org/dns-query` | Niemcy | Nieokreślone | Pro++ + TIF + NRD/DGA |
| **OpenBLD.net** | `https://ric.openbld.net/dns-query/hagezi` | Europa | Co godzinę | Pro + TIF w trybie RIC |
| **RethinkDNS** | `https://sky.rethinkdns.com/1:AAoACBAA` | Cloudflare | Raz w tygodniu | Pro + TIF |

!!! tip "Od czego zacząć, jeśli nie chcesz się rejestrować"

    Zacznij od **HaGeZi DNS** z serwera Falkenstein (`https://root.hagezi.org/dns-query`). Nie wymaga konta, działa w Europie, aktualizuje listy co kilka godzin. To najprostsza droga do Hagezi Pro + TIF. Jeśli chcesz samodzielnie wybrać listy, użyj generatora RethinkDNS na `https://rethinkdns.com/configure` albo DNSWarden na `https://dnswarden.com/customfilter.html`. Jeśli potrzebujesz logów i własnych reguł, wybierz **NextDNS**.

### Generatory własnych konfiguracji

Jeśli chcesz samodzielnie wybrać, które listy mają być aktywne, masz dwa narzędzia.

**RethinkDNS** oferuje generator konfiguracji pod adresem `https://rethinkdns.com/configure`. Możesz tam zaznaczyć dokładnie te listy, które Cię interesują (np. Hagezi Pro i Hagezi TIF), a następnie skopiować wygenerowany link **DoH** lub **DoT**. RethinkDNS udostępnia oba formaty – wystarczy kliknąć, żeby przełączyć między nimi. Zaleta: pełna kontrola. Wada: aktualizacje raz w tygodniu.

**DNSWarden** oferuje podobny generator pod adresem `https://dnswarden.com/customfilter.html`. Pozwala wybrać listy z predefiniowanego zestawu, w tym Hagezi Pro i TIF, i wygenerować własny link DoH, DoT lub DoQ. Nie wymaga rejestracji. DNSWarden udostępnia też gotowe presety, na przykład `https://dns.dnswarden.com/00000000000000000000018` dla Hagezi Pro + TIF.

### Inne opcje z własnym panelem

| Resolver | Adres DoH | Filtrowanie | Konto? |
|---|---|---|---|
| **NextDNS** | `https://dns.nextdns.io/twoj-id` | Pełna konfiguracja, własne listy, logi | Tak (darmowy plan, 300k zapytań) |
| **Control D** | `https://freedns.controld.com/x-hagezi-proplus` | Hagezi Pro Plus | Nie (darmowy preset) |
| **AdGuard DNS** | `https://dns.adguard-dns.com/dns-query` | Reklamy, trackery, malware | Nie |

**NextDNS** to najpotężniejsza opcja. W darmowym planie dostajesz 300 000 zapytań miesięcznie, co dla jednej osoby jest praktycznie nieosiągalne. Możesz wybierać listy blokujące, tworzyć własne reguły, przeglądać logi.

**Control D** w wersji darmowej nie ma panelu, ale udostępnia gotowe resolvery z listami Hagezi. Adres `x-hagezi-proplus` to bardzo agresywny zestaw, który blokuje reklamy, trackery, malware i phishing.

## Konfiguracja krok po kroku

### 1. Konto Proton VPN

Załóż darmowe konto na protonvpn.com. Nie musisz podawać danych osobowych. Wystarczy adres e-mail.

### 2. Plik WireGuard z Protona

Zaloguj się na `account.protonvpn.com/downloads`, wybierz WireGuard, a następnie wybierz serwer. Dla darmowego planu wybierz jeden z 10 dostępnych krajów. Polska jest jedną z opcji.

**Wybór serwera a IPv6:** Obsługa IPv6 w Proton VPN zależy od platformy. Oficjalnie IPv6 jest wspierane w rozszerzeniu przeglądarki oraz w kliencie na Linuksa. Na pozostałych platformach (Windows, macOS, iOS) Proton domyślnie blokuje cały wychodzący ruch IPv6, aby zapobiec wyciekom. Około 80% serwerów Proton jest kompatybilnych z IPv6. Jeśli chcesz korzystać z IPv6 przez tunel na Androidzie, wybierz serwer oznaczony jako IPv6 (np. `PL-FREE#17`). Serwer `CH-FREE#2` jest kompatybilny z IPv6, ale wymaga ręcznej konfiguracji adresu ULA (`fd54:...`) zamiast domyślnego adresu `2a07:...`.

Pobierz plik `.conf`. Nie musisz go edytować. WG Tunnel i tak użyje własnego DNS.

### 3. Konfiguracja WG Tunnel

Otwórz WG Tunnel i zaimportuj plik `.conf` z Protona.

Następnie przejdź do **Ustawienia → DNS settings** i ustaw:

- **Tunnel DNS mode:** `Encrypted`
- **Tunnel DNS Protocol:** `DoH`
- **Tunnel DNS Endpoint:** wklej adres wybranego resolvera, na przykład `https://root.hagezi.org/dns-query`
- **Transit DNS requests:** `Redirect` (przekierowuje zapytania do innych serwerów DNS na ten z tunelu)

Zapisz ustawienia.

### 4. Połączenie i weryfikacja

Połącz tunel. Następnie wejdź na `https://adblock.turtlecute.org/` i sprawdź, ile procent reklam i trackerów jest blokowanych. Powinieneś zobaczyć wynik powyżej 90%.

Możesz też wejść na `ipleak.net` i sprawdzić, czy DNS nie wycieka. Powinien być widoczny tylko resolver, którego używasz. Upewnij się, że na liście nie pojawia się adres DNS Twojego dostawcy internetu.

## Czego się spodziewać

**Blokowanie reklam i trackerów.** W zależności od wybranego resolvera i list, zablokujesz od 90 do 97 procent reklam i trackerów. Hagezi Pro + TIF daje najlepsze wyniki, ale może czasem zablokować coś, czego potrzebujesz. Wtedy dodaj domenę do wyjątków (jeśli resolver na to pozwala) albo wybierz mniej agresywną listę.

**Szyfrowany DNS.** Twoje zapytania DNS będą szyfrowane end-to-end. Proton nie zobaczy, o co pytasz. Operator sieci też nie.

**Stabilność połączenia.** WG Tunnel działa stabilnie, ale nie jest tak dojrzały jak standardowy WireGuard. W nowszych wersjach naprawiono problemy z baterią, a deweloper aktywnie rozwija projekt. Jeśli zauważysz problemy, wróć do standardowego klienta i zaakceptuj plain DNS.

## Podsumowanie

Darmowy Proton VPN to dobry tunel. Brakuje mu filtrowania DNS, ale można to obejść. WG Tunnel plus resolver DoH z listami Hagezi Pro + TIF daje Ci to, czego brakuje w darmowym planie: blokowanie reklam, trackerów, malware i phishingu, oraz szyfrowanie zapytań DNS przed wszystkimi pośrednikami.

Nie musisz płacić, żeby mieć prywatny i filtrowany DNS. Musisz tylko wiedzieć, jak go skonfigurować.
