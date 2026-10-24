---
title: Konfiguracja Przeglądarek
description: Rygorystyczne instrukcje utwardzania Brave na Androidzie i iOS. Ustawienia Tarcz, filtrowania treści, telemetrii i bezpiecznego DNS.
icon: lucide/settings-2
---

# Konfiguracja przeglądarek

!!! abstract "Podejście do konfiguracji"
    Poniższe instrukcje opisują rygorystyczną konfigurację przeglądarek pod kątem maksymalnego bezpieczeństwa i prywatności. Ustawienia te **nie zapewniają anonimowości w sieci** — do tego celu służy wyłącznie Tor Browser. Konfiguracja ma na celu ograniczenie profilowania, telemetrii i powierzchni ataku w codziennym korzystaniu z internetu.

!!! info "Projekt w ciągłym rozwoju"
    Ta strona jest na bieżąco aktualizowana. Obecnie pracuję nad rozbudową sekcji dotyczącej **Vanadium** (przeglądarki domyślnej dla GrapheneOS).

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

!!! note "Global Privacy Control i banery cookie"
    **Na Androidzie:** Global Privacy Control (GPC) jest flagą domyślnie włączoną (możesz to zweryfikować pod `brave://flags/#brave-global-privacy-control-enabled`). Banery zgody na pliki cookie są blokowane przez listę filtrów **EasyList Cookie**.
    
    **Na iOS:** Platforma nie obsługuje flag (brak dostępu do `brave://flags`), więc GPC jest zwykłym przełącznikiem. Warto jawnie włączyć **Enable Global Privacy Control** w sekcji *Shields & Privacy*. Działa on jako sygnał tylko dla JavaScript. Dodatkowo na iOS dostępne jest osobne ustawienie **Block Cookie Consent Notices**.

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

1. Implementacja Safe Browsing w Brave na Androidzie **nie** pośredniczy w żądaniach sieciowych. Oznacza to, że Twój adres IP może być widziany przez Google. Jeśli zależy Ci na prywatności, bezpieczniej jest polegać na systemowym filtrowaniu DNS (patrz sekcja poniżej).

## Autouzupełnianie, AI i dane lokalne

- [ ] Odznacz **Zapisywanie haseł / Menedżer haseł**
- [ ] Odznacz **Autouzupełnianie adresów i kart płatniczych**
- [ ] Odznacz **Ankiety Brave**
- [ ] Odznacz **Brave Rewards / Wallet / VPN / News** — warto ukryć ich ikony w ustawieniach wyglądu
- [ ] Odznacz **Sugestie w pasku adresu** (sekcja Leo AI)
- [ ] Odznacz **Sugestie w wyszukiwarce** (sekcja Wyszukiwarki)
- [ ] **Wyszukiwarka:** Ustaw **Brave Search** (lub inną prywatną) jako domyślną w `Ustawienia` → `Wyszukiwarki`. Brave Search nie profiluje użytkowników ani nie śledzi zapytań.

---

## Bezpieczny DNS

!!! tip "Dlaczego DNS ma znaczenie?"
    Nawet najbardziej rygorystyczna konfiguracja przeglądarki traci sens, jeśli Twój dostawca internetu (ISP) widzi niezabezpieczone zapytania DNS. Zamiast konfigurować to w samej przeglądarce, **przenieś ten ciężar na system operacyjny**. Ochroni to ruch globalnie, dla wszystkich aplikacji na telefonie.

!!! note "Dlaczego DNS nie zastępuje Safe Browsing 1:1?"
    DNS działa na poziomie **domeny** (np. blokuje `zlosliwa-domena.com`). Safe Browsing działa na poziomie **konkretnego adresu URL** (np. blokuje `bezpieczna-domena.com/phishing`). Jeśli złośliwa treść znajduje się na zaufanej domenie (np. w linku do fałszywego logowania), DNS jej nie zatrzyma. DNS to warstwa sieciowa (blokuje połączenie), Safe Browsing to warstwa aplikacji (weryfikuje reputację ścieżki). Rezygnacja z Safe Browsing na rzecz DNS to świadomy kompromis, a nie pełna zamiana.

**Polecani dostawcy (wybierz jednego):**

| Dostawca | Adres hosta | Opis |
| :--- | :--- | :--- |
| **Control D** | `p2.freedns.controld.com` | Darmowy resolver bez konta. Blokuje reklamy, trackery i malware. Nie przechowuje logów. |
| **Quad9** | `dns.quad9.net` | Maksymalna prywatność i ochrona przed malware. Szwajcarska fundacja non-profit, nie loguje adresów IP. |
| **AdGuard DNS** | `dns.adguard-dns.com` | Blokowanie reklam, trackerów i złośliwych domen. |
| **NextDNS** | *Wymaga własnego ID* | Zaawansowana, w pełni konfigurowalna zapora (wymaga konta i wygenerowania własnego adresu). |

=== "Android"

    W ustawieniach systemowych odszukaj opcję **Prywatny DNS** (zazwyczaj w zakładce *Sieć i internet*). Zamiast opcji automatycznej wybierz ręczne wprowadzanie nazwy hosta, wpisz adres wybranego dostawcy i zapisz zmiany.

=== "iOS"

    Pobierz profil konfiguracyjny od wybranego dostawcy (np. NextDNS oferuje plik `.mobileconfig`) i zatwierdź jego instalację w ustawieniach urządzenia.

---

## Vanadium (GrapheneOS)

!!! warning "Sekcja w przygotowaniu"
    Vanadium to utwardzona przeglądarka oparta na Chromium, dostarczana domyślnie z GrapheneOS. Jej filozofia różni się od Brave — zamiast rozbudowanych opcji konfiguracyjnych, stawia na **bezpieczne ustawienia domyślne (secure defaults)**.

**Kluczowe cechy Vanadium:**

| Cecha | Opis |
| :--- | :--- |
| **Brak rozszerzeń** | Podsystem rozszerzeń nie istnieje w Chromium na Androida, a GrapheneOS celowo go nie dodaje. Jest to podyktowane chęcią minimalizacji powierzchni ataku i zapobiegania fingerprintingowi. |
| **Wbudowane filtrowanie treści** | Vanadium posiada wbudowany bloker reklam i trackerów oparty na listach EasyList, EasyPrivacy, EasyList Adblock Warning Removal List oraz listach językowych. |
| **Utwardzenie jądra** | Domyślnie wyłączone JIT (Just-In-Time compilation), włączone partycjonowanie stanu sieci oraz kontrola przepływu sterowania (Control-flow integrity). |
| **Memory Tagging Extension (MTE)** | Vanadium jako pierwsza przeglądarka na świecie wykorzystuje MTE w środowisku produkcyjnym do ochrony sterty przed exploitami. |
| **Origin Keyed Processes** | Włączone domyślnie od wersji 141.0.7390.111.0, zapewniają lepszą izolację witryn (site isolation sandboxing). |

*Szczegółowa instrukcja konfiguracji Vanadium pojawi się wkrótce.*
