---
title: Konfiguracja przeglądarek
icon: lucide/settings-2
---

# Konfiguracja przeglądarek

Poniższe instrukcje opisują rygorystyczną konfigurację przeglądarek pod kątem maksymalnego bezpieczeństwa i prywatności. Ustawienia te **nie zapewniają jednak anonimowości w sieci** — do tego celu służy wyłącznie Tor Browser. Poniższa konfiguracja ma na celu ograniczenie profilowania, telemetrii i powierzchni ataku w codziennym korzystaniu z internetu.

## Brave (Android)

### Ustawienia Tarcz

Ustawienia znajdziesz w menu `⋮` → **Ustawienia** → **Brave Shields i prywatność**.

<div class="annotate" markdown>

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

Brave pozwala na wybór dodatkowych filtrów treści. Odradzam korzystanie z tej funkcji. Używanie dodatkowych list sprawi, że będziesz się wyróżniać na tle innych użytkowników Brave, a w przypadku exploita, może to zwiększyć powierzchnię ataku.
</details>

- [x] Wybierz **Karty witryny zamknięte** w sekcji *Auto Shred*

</div>

1. Ta opcja wyłącza JavaScript, co „zepsuje" wiele stron. Aby przywrócić działanie zaufanej witryny, kliknij ikonę Tarczy w pasku adresu i odznacz blokowanie skryptów w sekcji *Kontrola zaawansowana*.

## Pozostałe ustawienia prywatności

<div class="annotate" markdown>

- [x] (Opcjonalnie) Wybierz **Brak ochrony** w sekcji *Bezpieczne przeglądanie (Safe Browsing)* (1)
- [x] Wybierz **Wyłącz nieobsługiwany przez serwer proxy protokół UDP** w sekcji *WebRTC*
- [ ] Odznacz **Zezwalaj witrynom na sprawdzanie zapisanych metod płatności**
- [x] Wybierz opcję wyłączającą przyspieszanie stron w sekcji *Optymalizacja JavaScript*
- [x] Zaznacz **Zamykaj karty przy wyjściu**
- [ ] Odznacz **P3A (Analiza produktu) oraz raporty diagnostyczne**
- [ ] Odznacz **Codzienny ping użycia**

</div>

1. Implementacja Safe Browsing w Brave na Androidzie **nie** pośredniczy w żądaniach sieciowych. Oznacza to, że Twój adres IP może być widziany przez Google.

## Autouzupełnianie i dane lokalne

- [ ] Odznacz **Zapisywanie haseł / Menedżer haseł**
- [ ] Odznacz **Autouzupełnianie adresów i kart płatniczych**
- [ ] Odznacz **Ankiety Brave**
- [ ] Odznacz **Brave Rewards / Wallet / VPN / News** — warto ukryć ich ikony w ustawieniach wyglądu

## Leo AI

Ustawienia znajdziesz w menu `⋮` → **Ustawienia** → **Leo AI**.

- [ ] Odznacz **Sugestie w pasku adresu**

## Wyszukiwarki

Ustawienia znajdziesz w menu `⋮` → **Ustawienia** → **Wyszukiwarki**.

- [ ] Odznacz **Sugestie wyszukiwania**

## Bezpieczny DNS

Nawet najbardziej rygorystyczna konfiguracja przeglądarki traci sens, jeśli Twój dostawca internetu widzi niezabezpieczone zapytania DNS. Zaleca się skonfigurowanie prywatnego DNS w ustawieniach systemu Android, co chroni ruch globalnie, dla wszystkich aplikacji.

- **Control D** (`p2.freedns.controld.com`) — darmowy resolver bez konta, blokuje reklamy, trackery i malware. Nie przechowuje logów. Usługa jest tworzona przez zespół Windscribe, znanego dostawcę VPN.
- **Quad9** (`dns.quad9.net`) — maksymalna prywatność i ochrona przed malware. Szwajcarska fundacja non-profit, nie loguje adresów IP. Nie filtruje reklam.
- **AdGuard DNS** (`dns.adguard-dns.com`) — blokowanie reklam, trackerów i złośliwych domen.
- **NextDNS** — zaawansowana, w pełni konfigurowalna zapora (wymaga konta).
