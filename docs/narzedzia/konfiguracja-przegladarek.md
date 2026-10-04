---
title: Konfiguracja przeglądarek
icon: lucide/settings-2
---

# Konfiguracja przeglądarek

Poniższe instrukcje opisują rygorystyczną konfigurację przeglądarek pod kątem maksymalnego bezpieczeństwa i prywatności. Ustawienia te **nie zapewniają jednak anonimowości w sieci** — do tego celu służy wyłącznie Tor Browser. Poniższa konfiguracja ma na celu ograniczenie profilowania, telemetrii i powierzchni ataku w codziennym korzystaniu z internetu.

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

<div class="annotate" markdown>

=== "Android"

    - [x] (Opcjonalnie) Wybierz **Brak ochrony** w sekcji *Bezpieczne przeglądanie (Safe Browsing)* (1)
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

</div>

1. Implementacja Safe Browsing w Brave na Androidzie **nie** pośredniczy w żądaniach sieciowych. Oznacza to, że Twój adres IP może być widziany przez Google.

## Autouzupełnianie i dane lokalne

- [ ] Odznacz **Zapisywanie haseł / Menedżer haseł**
- [ ] Odznacz **Autouzupełnianie adresów i kart płatniczych**
- [ ] Odznacz **Ankiety Brave**
- [ ] Odznacz **Brave Rewards / Wallet / VPN / News** — warto ukryć ich ikony w ustawieniach wyglądu

## Leo AI

Ustawienia znajdziesz w:

=== "Android"

    Menu `⋮` → **Ustawienia** → **Leo AI**.

    - [ ] Odznacz **Sugestie w pasku adresu**

=== "iOS"

    Menu `⋯` → **Wszystkie ustawienia** → **Leo AI**.

    - [ ] Odznacz **Show In Quick Search Engine Bar**

## Wyszukiwarki

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

- **Control D** (`p2.freedns.controld.com`) — darmowy resolver bez konta, blokuje reklamy, trackery i malware. Nie przechowuje logów. Usługa jest tworzona przez zespół Windscribe, znanego dostawcę VPN.
- **Quad9** (`dns.quad9.net`) — maksymalna prywatność i ochrona przed malware. Szwajcarska fundacja non-profit, nie loguje adresów IP. Nie filtruje reklam.
- **AdGuard DNS** (`dns.adguard-dns.com`) — blokowanie reklam, trackerów i złośliwych domen.
- **NextDNS** — zaawansowana, w pełni konfigurowalna zapora (wymaga konta).

=== "Android"

    W ustawieniach systemowych odszukaj opcję **Prywatny DNS** (zazwyczaj w zakładce *Sieć i internet*). Zamiast opcji automatycznej wybierz ręczne wprowadzanie nazwy hosta, wpisz adres wybranego dostawcy i zapisz zmiany.

=== "iOS"

    Pobierz profil konfiguracyjny od wybranego dostawcy (np. NextDNS oferuje plik `.mobileconfig`) i zatwierdź jego instalację w ustawieniach urządzenia.
