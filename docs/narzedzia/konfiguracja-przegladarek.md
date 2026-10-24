---
title: Konfiguracja Przeglądarek
description: Autorski zestaw rekomendacji utwardzania Brave na Androidzie i iOS. Ustawienia Tarcz, filtrowania treści, telemetrii, bezpiecznego DNS oraz kompromisów bezpieczeństwa.
icon: lucide/settings-2
---

# Konfiguracja przeglądarek

Poniższe instrukcje opisują rygorystyczną konfigurację przeglądarek pod kątem maksymalnego bezpieczeństwa i prywatności. Ustawienia te **nie zapewniają jednak anonimowości w sieci** — do tego celu służy wyłącznie Tor Browser. Konfiguracja ma na celu ograniczenie profilowania, telemetrii i powierzchni ataku w codziennym korzystaniu z internetu.

# Brave

## Ustawienia Tarcz

Ustawienia znajdziesz w:

=== "Android"

    Menu `⋮` → **Ustawienia** → **Brave Shields i prywatność**.

=== "iOS"

    Menu `⋯` → **Wszystkie ustawienia** → **Shields & Privacy**.

### Globalne ustawienia Tarcz

<div class="annotate" markdown>

=== "Android"

    - [x] Wybierz **Agresywne** w sekcji *Blokowanie trackerów i reklam*
    - [x] Wybierz **Auto-przekierowywanie stron AMP**
    - [x] Wybierz **Auto-przekierowywanie adresów śledzących**
    - [x] Wybierz **Wymagaj, aby wszystkie połączenia używały HTTPS (rygorystyczne)**
    - [x] (Opcjonalnie) Wybierz **Blokowanie skryptów** (1)
    - [x] Wybierz **Blokuj pliki cookie z innych witryn**
    - [x] Wybierz **Blokowanie fingerprintingu**
    - [x] Wybierz **Zapobiegaj fingerprintingowi przez ustawienia języka**

    <details class="warning" markdown>
    <summary>Używaj domyślnych list filtrów</summary>

    Brave pozwala na wybór dodatkowych filtrów treści w menu **Filtrowanie treści** lub na wewnętrznej stronie `brave://adblock`. Odradzam korzystanie z tej funkcji. Używanie dodatkowych list sprawi, że będziesz się wyróżniać na tle innych użytkowników Brave, a w przypadku exploita, może to zwiększyć powierzchnię ataku.
    </details>

    - [x] Wybierz **Karty witryny zamknięte** w sekcji *Auto Shred*

=== "iOS"

    - [x] Wybierz **Agresywne** w sekcji *Trackers & Ads Blocking*
    - [x] Wybierz **Rygorystyczne** w sekcji *Upgrade Connections to HTTPS*
    - [x] Wybierz **Auto-Redirect AMP pages**
    - [x] Wybierz **Auto-Redirect Tracking URLs**
    - [x] (Opcjonalnie) Wybierz **Block Scripts** (1)
    - [x] Wybierz **Block Fingerprinting**
    - [x] Wybierz **Site Tabs Closed** w sekcji *Auto Shred*

    <details class="warning" markdown>
    <summary>Używaj domyślnych list filtrów</summary>

    Brave pozwala na wybór dodatkowych filtrów treści w menu **Content Filtering**. Odradzam korzystanie z tej funkcji. Używanie dodatkowych list sprawi, że będziesz się wyróżniać na tle innych użytkowników Brave, a w przypadku exploita, może to zwiększyć powierzchnię ataku.
    </details>

</div>

1. Ta opcja wyłącza JavaScript, co „zepsuje" wiele stron. Aby przywrócić działanie zaufanej witryny, kliknij ikonę Tarczy w pasku adresu i odznacz blokowanie skryptów w sekcji *Kontrola zaawansowana*.

## Pozostałe ustawienia prywatności

=== "Android"

    - [x] (Opcjonalnie) Wybierz **Brak ochrony** w sekcji **Bezpieczne przeglądanie (Safe Browsing)**
    - [x] Wybierz **Wyłącz nieobsługiwany przez serwer proxy protokół UDP** w sekcji *WebRTC*
    - [ ] Odznacz **Zezwalaj witrynom na sprawdzanie zapisanych metod płatności**
    - [x] Wybierz opcję wyłączającą przyspieszanie stron w sekcji *Optymalizacja JavaScript*
    - [x] Zaznacz **Zamykaj karty przy wyjściu**
    - [ ] Odznacz **P3A (Analiza produktu) oraz raporty diagnostyczne**
    - [ ] Odznacz **Codzienny ping użycia**

=== "iOS"

    - [ ] Odznacz **Allow Privacy-Preserving Product Analytics (P3A)**
    - [ ] Odznacz **Automatically send daily usage ping to Brave**
    - [x] Zaznacz **Close tabs on exit** w sekcji *Auto Shred*

<details class="info" markdown>
<summary>Jak działa Safe Browsing i dlaczego nie zastąpi go DNS? (rozwiń)</summary>

Safe Browsing to usługa reputacyjna, która weryfikuje **pełne adresy URL** (a nie tylko nazwy domen) pod kątem list zagrożeń — phishingowych, hostujących malware czy niechciane oprogramowanie. W przeglądarce działa ona warstwowo: przeglądarka okresowo pobiera skróty lokalnej listy, a przy trafieniu może odpytać serwer o szczegóły. Dzięki temu ochrona obejmuje ścieżki i parametry, których DNS nie widzi.

Na Androidzie implementacja Safe Browsing w Brave **nie pośredniczy w żądaniach sieciowych** tak jak w wersji desktopowej. Oznacza to, że Twój adres IP może być widoczny dla Google przy zapytaniach weryfikacyjnych. To właśnie ten kompromis — realna ochrona przed znanymi zagrożeniami w zamian za częściowe ujawnienie metadanych dostawcy usługi — sprawia, że wyłączenie Safe Browsing jest **świadomą decyzją**, a nie oczywistością.

DNS (w tym szyfrowany DoH/DoT) działa wyłącznie na poziomie **nazwy domeny**. Może blokować całe domeny z listy, ale nie sprawdzi, czy konkretny artykuł lub plik do pobrania na zaufanej domenie został właśnie przejęty i hostuje malware. Co więcej, dostawcy DNS tacy jak NextDNS czy Control D oferują wprawdzie filtrowanie oparte na danych Safe Browsing, ale jest to **inna warstwa** — działa na domenach, a nie na pełnych adresach URL. Nie jest więc zamiennikiem, lecz uzupełnieniem.

**Rekomendacja:** Jeśli priorytetem jest ochrona przed phishingiem i malware, pozostaw Safe Browsing włączony, akceptując kompromis. Jeśli priorytetem jest minimalizacja kontaktu z Google, wyłącz go świadomie i polegaj na warstwie DNS oraz ostrożności. Nie traktuj DNS jako „zamiennika” Safe Browsing — to nieprawda.
</details>

## Autouzupełnianie, AI i wyszukiwanie

Poniższe ustawienia ograniczają gromadzenie danych lokalnych oraz funkcje pomocnicze, które mogą wysyłać zapytania do zewnętrznych usług.

### Autouzupełnianie i dane lokalne

- [ ] Odznacz **Zapisywanie haseł / Menedżer haseł**
- [ ] Odznacz **Autouzupełnianie adresów i kart płatniczych**
- [ ] Odznacz **Ankiety Brave**
- [ ] Odznacz **Brave Rewards / Wallet / VPN / News** — warto ukryć ich ikony w ustawieniach wyglądu

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
