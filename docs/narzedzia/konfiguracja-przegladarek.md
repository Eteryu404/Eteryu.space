---
title: Konfiguracja Przeglądarek
description: Autorski zestaw rekomendacji utwardzania Brave na Androidzie i iOS. Ustawienia Tarcz, filtrowania treści, telemetrii, bezpiecznego DNS oraz kompromisów bezpieczeństwa.
icon: lucide/settings-2
---

# Konfiguracja przeglądarek

Poniższe instrukcje opisują rygorystyczną konfigurację przeglądarek pod kątem maksymalnego bezpieczeństwa i prywatności. Ustawienia te **nie zapewniają jednak anonimowości w sieci** — do tego celu służy wyłącznie Tor Browser. Konfiguracja ma na celu ograniczenie profilowania, telemetrii i powierzchni ataku w codziennym korzystaniu z internetu.

## Bezpieczny DNS

Nawet najbardziej rygorystyczna konfiguracja przeglądarki traci sens, jeśli Twój dostawca internetu widzi niezabezpieczone zapytania DNS. Zaleca się skonfigurowanie prywatnego DNS w ustawieniach systemu, co chroni ruch globalnie, dla wszystkich aplikacji.

Poniżej zestawienie sprawdzonych resolverów. Wybór zależy od tego, czy ważniejsza jest dla Ciebie filtracja reklam, maksymalna prywatność, czy zaawansowana konfiguracja.

| Dostawca | Adresy (DoH / DoT) | Filtrowanie i uwagi |
|---|---|---|
| **Control D** | `p2.freedns.controld.com` | Reklamy, trackery, malware. Darmowy resolver bez konta. Tworzony przez zespół Windscribe. Nie przechowuje logów w planie darmowym. |
| **Quad9** | `dns.quad9.net` | Malware i phishing (opcjonalnie). Szwajcarska fundacja non-profit. **Nie loguje adresów IP.** Nie filtruje reklam. |
| **AdGuard DNS** | `dns.adguard-dns.com` | Reklamy, trackery, złośliwe domeny. Prosty w konfiguracji. Zależnie od planu może prowadzić logi. |
| **NextDNS** | Konfigurowany indywidualnie | Pełna personalizacja i zaawansowana zapora DNS. Wymaga konta. Logi konfigurowalne przez użytkownika. |

=== "Android"

    W ustawieniach systemowych odszukaj opcję **Prywatny DNS** (zazwyczaj w zakładce *Sieć i internet*). Zamiast opcji automatycznej wybierz ręczne wprowadzanie nazwy hosta, wpisz adres wybranego dostawcy i zapisz zmiany.

=== "iOS"

    Pobierz profil konfiguracyjny od wybranego dostawcy (np. NextDNS oferuje plik `.mobileconfig`) i zatwierdź jego instalację w ustawieniach urządzenia.

---

# Brave

## Wprowadzenie

Ustawienia znajdziesz w:

=== "Android"

    Menu `⋮` → **Ustawienia** → **Brave Shields i prywatność**.

=== "iOS"

    Menu `⋯` → **Wszystkie ustawienia** → **Shields & Privacy**.

## Ochrona przed śledzeniem i reklamami

Włącz podstawowe mechanizmy blokujące inwigilację. To fundament prywatności w Brave.

1.  W sekcji *Blokowanie trackerów i reklam* wybierz poziom **Agresywny**.
2.  Włącz **Blokowanie fingerprintingu**.
3.  Włącz **Zapobieganie fingerprintingowi przez ustawienia języka**.

!!! warning "Używaj domyślnych list filtrów"
    Brave pozwala na wybór dodatkowych filtrów treści w menu **Filtrowanie treści** lub na wewnętrznej stronie `brave://adblock`. Odradzam korzystanie z tej funkcji. Trzymanie się domyślnych list jest bezpieczniejsze. Im więcej niestandardowych reguł dodasz, tym bardziej Twoja przeglądarka będzie się wyróżniać na tle innych. W skrajnym przypadku, źle skonstruowane dodatkowe listy mogą nawet zwiększyć powierzchnię ataku w razie wystąpienia luki w zabezpieczeniach.

## Bezpieczeństwo połączeń

Zadbaj o to, aby Twoje połączenia były szyfrowane i pozbawione pośredników.

1.  Włącz **Wymagaj, aby wszystkie połączenia używały HTTPS (rygorystyczne)**.
2.  Włącz **Auto-przekierowywanie stron AMP**.
3.  Włącz **Auto-przekierowywanie adresów śledzących**.
4.  W sekcji *WebRTC* wybierz **Wyłącz nieobsługiwany przez serwer proxy protokół UDP**.

## Minimalizacja danych i prywatność

Ogranicz ilość danych, które przeglądarka przechowuje lub wysyła.

1.  Włącz **Blokuj pliki cookie z innych witryn**.
2.  Włącz **Zamykaj karty przy wyjściu** (lub *Auto Shred*).
3.  Odznacz **Zapisywanie haseł / Menedżer haseł**.
4.  Odznacz **Autouzupełnianie adresów i kart płatniczych**.
5.  Odznacz **Ankiety Brave**.
6.  Odznacz **P3A (Analiza produktu) oraz raporty diagnostyczne**.
7.  Odznacz **Codzienny ping użycia**.
8.  Odznacz **Brave Rewards / Wallet / VPN / News** — warto ukryć ich ikony w ustawieniach wyglądu.
9.  Odznacz **Zezwalaj witrynom na sprawdzanie zapisanych metod płatności**.

### Safe Browsing (opcjonalnie)

To świadoma decyzja o kompromisie między bezpieczeństwem a prywatnością.

=== "Android"

    - [x] (Opcjonalnie) Wybierz **Brak ochrony** w sekcji **Bezpieczne przeglądanie (Safe Browsing)**

    <details class="info" markdown>
    <summary>Jak działa Safe Browsing i dlaczego nie zastąpi go DNS? (rozwiń)</summary>

    Safe Browsing to usługa reputacyjna, która weryfikuje **pełne adresy URL** (a nie tylko nazwy domen) pod kątem list zagrożeń — phishingowych, hostujących malware czy niechciane oprogramowanie. W przeglądarce działa ona warstwowo: przeglądarka okresowo pobiera skróty lokalnej listy, a przy trafieniu może odpytać serwer o szczegóły. Dzięki temu ochrona obejmuje ścieżki i parametry, których DNS nie widzi.

    Na Androidzie implementacja Safe Browsing w Brave **nie pośredniczy w żądaniach sieciowych** tak jak w wersji desktopowej. Oznacza to, że Twój adres IP może być widoczny dla Google przy zapytaniach weryfikacyjnych. To właśnie ten kompromis — realna ochrona przed znanymi zagrożeniami w zamian za częściowe ujawnienie metadanych dostawcy usługi — sprawia, że wyłączenie Safe Browsing jest **świadomą decyzją**, a nie oczywistością.

    DNS (w tym szyfrowany DoH/DoT) działa wyłącznie na poziomie **nazwy domeny**. Może blokować całe domeny z listy, ale nie sprawdzi, czy konkretny artykuł lub plik do pobrania na zaufanej domenie został właśnie przejęty i hostuje malware. Co więcej, dostawcy DNS tacy jak NextDNS czy Control D oferują wprawdzie filtrowanie oparte na danych Safe Browsing, ale jest to **inna warstwa** — działa na domenach, a nie na pełnych adresach URL. Nie jest więc zamiennikiem, lecz uzupełnieniem.

    **Rekomendacja:** Jeśli priorytetem jest ochrona przed phishingiem i malware, pozostaw Safe Browsing włączony, akceptując kompromis. Jeśli priorytetem jest minimalizacja kontaktu z Google, wyłącz go świadomie i polegaj na warstwie DNS oraz ostrożności. Nie traktuj DNS jako „zamiennika” Safe Browsing — to nieprawda.
    </details>

=== "iOS"

    - [ ] (Opcjonalnie) Odznacz **Block Dangerous Sites** w sekcji *Shields & Privacy*

    <details class="info" markdown>
    <summary>Jak działa ochrona przed złośliwymi stronami na iOS? (rozwiń)</summary>

    Na iOS odpowiednikiem Safe Browsing jest opcja **Block Dangerous Sites**. Podobnie jak na Androidzie, ochrona ta opiera się na danych Google (lub Tencent w niektórych regionach), ale jest realizowana przez systemowy mechanizm `WKWebView`. Oznacza to, że **żądania weryfikacyjne nie przechodzą przez serwer proxy Brave** i mogą być widoczne dla Apple, Google lub Tencent. Wyłączenie tej opcji jest świadomym kompromisem między bezpieczeństwem a prywatnością, analogicznym do decyzji podejmowanej na Androidzie.
    </details>

## Funkcje pomocnicze (AI, wyszukiwanie, autouzupełnianie)

Ogranicz funkcje, które mogą wysyłać zapytania do zewnętrznych usług.

### Leo AI

Ustawienia znajdziesz w:

=== "Android"

    Menu `⋮` → **Ustawienia** → **Leo AI**.

    - [ ] Odznacz **Sugestie w pasku adresu**

=== "iOS"

    Menu `⋯` → **Wszystkie ustawienia** → **Leo AI**.

    - [ ] Odznacz **Show In Quick Search Engine Bar**

### Wyszukiwarki

Ustawienia znajdziesz w:

=== "Android"

    Menu `⋮` → **Ustawienia** → **Wyszukiwarki**.

    - [ ] Odznacz **Sugestie wyszukiwania**

=== "iOS"

    Menu `⋯` → **Wszystkie ustawienia** → **Search engines**.

    - [ ] Odznacz **Show In Quick Search Engine Bar**

---

## Vanadium (WIP)

!!! warning "Status: Work in progress"
    Poniższa sekcja jest w fazie opracowywania. Ustawienia mogą ulec zmianie wraz z aktualizacjami GrapheneOS i Vanadium.

Vanadium to domyślna, utwardzona przeglądarka oparta na Chromium, dostarczana z GrapheneOS. Jej filozofia bezpieczeństwa jest odmienna od Brave: zamiast rozbudowanego ekosystemu funkcji prywatności, stawia na **bezpieczeństwo fundamentu** — ścisłą izolację procesów, ograniczenie dynamicznego generowania kodu i minimalizację powierzchni ataku.

### Główne cechy bezpieczeństwa

- **Wyłączony JIT dla JavaScript** — kompilacja Just-In-Time jest domyślnie zablokowana, co znacząco utrudnia wykorzystanie błędów w silniku JS. W razie potrzeby można ją włączyć per-site dla zaufanych witryn wymagających dużej wydajności.
- **Seccomp-bpf** — mechanizmy jądra systemu blokujące dynamiczne generowanie kodu w procesach innych niż piaskownica renderera.

### Wbudowany bloker treści

Vanadium posiada wbudowany bloker oparty na listach **EasyList** (EasyList, EasyPrivacy, EasyList Adblock Warning Removal List oraz listy językowe dopasowywane do języka interfejsu).

- Działa jako *subresource filtering*: blokuje żądania sieciowe do znanych źródeł reklam i trackerów.
- **Ograniczenia:** nie zapewnia filtrowania kosmetycznego ani wstrzykiwania scriptletów. Reklamy osadzane dynamicznie (np. w odtwarzaczu YouTube) mogą pozostać widoczne. W tym aspekcie jest słabszy od Brave Shields, ale nadal skuteczniejszy niż samo filtrowanie DNS.

Wkrótce uzupełnię tę sekcję o pełną listę rekomendowanych ustawień. Tymczasem warto zapoznać się z [zaleceniami społeczności Privacy Guides dla Vanadium](https://discuss.privacyguides.net/t/vanadium-recommended-settings/27338), pamiętając, że są to rekomendacje zewnętrzne, a nie część niniejszego przewodnika.
