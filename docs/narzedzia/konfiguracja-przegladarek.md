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
    - [x] (Opcjonalnie) Wybierz **Blokowanie skryptów**
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
    - [x] (Opcjonalnie) Wybierz **Block Scripts**
    - [x] Wybierz **Block Fingerprinting**
    - [x] Wybierz **Site Tabs Closed** w sekcji *Auto Shred*

    <details class="warning" markdown>
    <summary>Używaj domyślnych list filtrów</summary>

    Brave pozwala na wybór dodatkowych filtrów treści w menu **Content Filtering**. Odradzam korzystanie z tej funkcji. Używanie dodatkowych list sprawi, że będziesz się wyróżniać na tle innych użytkowników Brave, a w przypadku exploita, może to zwiększyć powierzchnię ataku.
    </details>

</div>

!!! note "Uwaga o blokowaniu skryptów"
    Opcja blokowania skryptów wyłącza JavaScript, co „zepsuje" wiele stron. Aby przywrócić działanie zaufanej witryny, kliknij ikonę Tarczy w pasku adresu i odznacz blokowanie skryptów w sekcji *Kontrola zaawansowana*.

## Pozostałe ustawienia prywatności

<div class="annotate" markdown>

=== "Android"

    - [x] (Opcjonalnie) Wybierz **Brak ochrony** w sekcji *Bezpieczne przeglądanie (Safe Browsing)*
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

!!! warning "Dlaczego wyłączenie Safe Browsing ma sens na Androidzie?"
    W przeciwieństwie do wersji desktopowej, implementacja Safe Browsing w Brave na Androidzie **nie pośredniczy** w żądaniach sieciowych. Oznacza to, że każde sprawdzenie adresu URL może zostać wykonane bezpośrednio z Twojego urządzenia, ujawniając Twój adres IP firmie Google. Jeśli zależy Ci na prywatności, bezpieczniej jest polegać na systemowym filtrowaniu DNS (patrz sekcja poniżej) lub zaakceptować to ryzyko, mając świadomość kompromisu.

## Autouzupełnianie, AI i dane lokalne

- [ ] Odznacz **Zapisywanie haseł / Menedżer haseł**
- [ ] Odznacz **Autouzupełnianie adresów i kart płatniczych**
- [ ] Odznacz **Ankiety Brave**
- [ ] Odznacz **Brave Rewards / Wallet / VPN / News** — warto ukryć ich ikony w ustawieniach wyglądu
- [ ] Odznacz **Sugestie w pasku adresu** (sekcja Leo AI)
- [ ] Odznacz **Sugestie wyszukiwania** (sekcja Wyszukiwarki)

---

## Bezpieczny DNS

!!! tip "Dlaczego DNS ma znaczenie?"
    Nawet najbardziej rygorystyczna konfiguracja przeglądarki traci sens, jeśli Twój dostawca internetu (ISP) widzi niezabezpieczone zapytania DNS. Zamiast konfigurować to w samej przeglądarce, **przenieś ten ciężar na system operacyjny**. Ochroni to ruch globalnie, dla wszystkich aplikacji na telefonie.

Polecani dostawcy (wybierz jednego):
- **Control D** (`p2.freedns.controld.com`) — darmowy resolver bez konta, blokuje reklamy, trackery i malware. Nie przechowuje logów.
- **Quad9** (`dns.quad9.net`) — maksymalna prywatność i ochrona przed malware (szwajcarska fundacja non-profit).
- **AdGuard DNS** (`dns.adguard-dns.com`) — blokowanie reklam, trackerów i złośliwych domen.
- **NextDNS** — zaawansowana, w pełni konfigurowalna zapora (wymaga konta).

=== "Android"

    W ustawieniach systemowych odszukaj opcję **Prywatny DNS** (zazwyczaj w zakładce *Sieć i internet*). Zamiast opcji automatycznej wybierz ręczne wprowadzanie nazwy hosta, wpisz adres wybranego dostawcy i zapisz zmiany.

=== "iOS"

    Pobierz profil konfiguracyjny od wybranego dostawcy (np. NextDNS oferuje plik `.mobileconfig`) i zatwierdź jego instalację w ustawieniach urządzenia.

---

## Vanadium (GrapheneOS)

!!! warning "Sekcja w przygotowaniu"
    Vanadium to utwardzona przeglądarka oparta na Chromium, dostarczana domyślnie z GrapheneOS. Jej filozofia różni się od Brave — zamiast rozbudowanych opcji konfiguracyjnych, stawia na **bezpieczne ustawienia domyślne (secure defaults)**.

**Kluczowe cechy Vanadium:**
- **Brak rozszerzeń:** Podsystem rozszerzeń nie istnieje w Chromium na Androida, a GrapheneOS celowo go nie dodaje. Jest to podyktowane chęcią minimalizacji powierzchni ataku i zapobiegania fingerprintingowi.
- **Wbudowane filtrowanie treści:** Vanadium posiada wbudowany bloker reklam i trackerów oparty na listach EasyList i EasyPrivacy.
- **Utwardzenie jądra:** Domyślnie wyłączone JIT (Just-In-Time compilation), włączone partycjonowanie stanu sieci oraz kontrola przepływu sterowania (Control-flow integrity).

*Szczegółowa instrukcja konfiguracji Vanadium pojawi się wkrótce.*
