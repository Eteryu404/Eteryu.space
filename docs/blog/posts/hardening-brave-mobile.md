---
title: "Hardening Brave (Mobile): kompletna konfiguracja bezpieczeństwa"
date: 2026-08-21
authors:
  - Eteryu
categories:
  - Prywatność
  - Android
  - Narzędzia
---

*Ten poradnik powstał w odpowiedzi na prośbę o konfigurację przeglądarki ze szczególnym naciskiem na **bezpieczeństwo**. Z tego względu zalecenia są bardzo rygorystyczne – zakładają m.in. całkowite wyłączenie autouzupełniania danych, kasowanie sesji po zamknięciu oraz globalną blokadę skryptów. Taka konfiguracja znacznie podnosi odporność na ataki, ale wymaga zmiany nawyków (np. ręcznego zezwalania na skrypty na zaufanych stronach). Jeśli zależy Ci na większej wygodzie, możesz traktować poniższą listę jako punkt wyjścia i elastycznie ją dostosować.*

<!-- more -->

Tor Browser to jedyny sposób na prawdziwie anonimowe przeglądanie internetu. Korzystając z Brave, zalecamy zmianę poniższych ustawień, aby chronić swoją prywatność przed określonymi podmiotami. Warto jednak pamiętać, że każda przeglądarka poza Tor Browser będzie w pewnym stopniu możliwa do wyśledzenia przez kogoś.

## Ustawienia Tarcz (Brave Shields & privacy)

Ustawienia znajdziesz w menu `⋮` → **Ustawienia** → **Brave Shields i prywatność**.

### Globalne ustawienia Tarcz

Brave zawiera wbudowane mechanizmy anty-fingerprintingowe w funkcji Tarcz. Zaleca się skonfigurowanie tych opcji globalnie, dla wszystkich odwiedzanych stron. Poniższe ustawienia można w razie potrzeb obniżyć dla pojedynczych witryn, ale domyślnie rekomendowane są następujące wartości:

<div class="annotate" markdown>

- [x] Wybierz **Agresywne** w sekcji *Blokowanie trackerów i reklam*
- [x] Wybierz **Auto-przekierowywanie stron AMP**
- [x] Wybierz **Auto-przekierowywanie adresów śledzących**
- [x] Wybierz **Wymagaj, aby wszystkie połączenia używały HTTPS (rygorystyczne)** w sekcji *Uaktualniaj połączenia do HTTPS*
- [x] (Opcjonalnie) Wybierz **Blokowanie skryptów** (1)
- [x] Wybierz **Blokuj pliki cookie z innych witryn** w sekcji *Blokowanie plików cookie*
- [x] Wybierz **Blokowanie fingerprintingu**
- [x] Wybierz **Zapobiegaj fingerprintingowi przez ustawienia języka**

<details class="warning" markdown>
<summary>Używaj domyślnych list filtrów</summary>

Brave pozwala na wybór dodatkowych filtrów treści w menu **Filtrowanie treści** lub na wewnętrznej stronie `brave://adblock`. **Odradzamy korzystanie z tej funkcji.** Zamiast tego warto pozostać przy domyślnych listach filtrów. Używanie dodatkowych list sprawi, że będziesz się wyróżniać na tle innych użytkowników Brave, a w przypadku exploita w Brave i dodania złośliwej reguły do jednej z używanych list, może to również zwiększyć powierzchnię ataku.

</details>

- [x] Wybierz **Karty witryny zamknięte** w sekcji *Auto Shred*

</div>

1. Ta opcja wyłącza JavaScript, co „zepsuje" wygląd i działanie bardzo wielu stron. Aby przywrócić działanie zaufanej witryny, kliknij ikonę Tarczy (Brave Shields) w pasku adresu i odznacz blokowanie skryptów w sekcji *Kontrola zaawansowana*.

### Pozostałe ustawienia prywatności

<div class="annotate" markdown>

- [x] (Opcjonalnie) Wybierz **Brak ochrony** w sekcji *Bezpieczne przeglądanie (Safe Browsing)* (1)
- [x] Wybierz **Wyłącz nieobsługiwany przez serwer proxy protokół UDP** w sekcji *Zasady obsługi adresów IP przez WebRTC*
- [ ] Odznacz **Zezwalaj witrynom na sprawdzanie zapisanych metod płatności**
- [x] Wybierz opcję wyłączającą przyspieszanie stron w sekcji *Optymalizacja i bezpieczeństwo JavaScript*
- [x] Zaznacz **Zamykaj karty przy wyjściu (Close tabs on exit)**
- [ ] Odznacz **P3A (Analiza produktu) oraz raporty diagnostyczne**
- [ ] Odznacz **Codzienny ping użycia**

</div>

1. Implementacja Safe Browsing w Brave na Androidzie **nie** pośredniczy w żądaniach sieciowych do Safe Browsing, tak jak wersja desktop. Oznacza to, że Twój adres IP może być widziany (i logowany) przez Google.

### Autouzupełnianie i dane lokalne

- [ ] Odznacz **Zapisywanie haseł / Menedżer haseł**
- [ ] Odznacz **Autouzupełnianie adresów i kart płatniczych**
- [ ] Odznacz **Ankiety Brave (Brave surveys)**
- [ ] Odznacz **Brave Rewards / Wallet / VPN / News** — warto dodatkowo ukryć ich ikony w ustawieniach wyglądu

### Leo AI

Ustawienia znajdziesz w menu `⋮` → **Ustawienia** → **Leo AI**.

- [ ] Odznacz **Sugestie w pasku adresu**

### Wyszukiwarki

Ustawienia znajdziesz w menu `⋮` → **Ustawienia** → **Wyszukiwarki**.

- [ ] Odznacz **Sugestie wyszukiwania**

## Bezpieczny DNS

Nawet najbardziej rygorystyczna konfiguracja przeglądarki traci sens, jeśli Twój dostawca internetu wciąż widzi niezabezpieczone zapytania DNS. Zamiast włączać bezpieczny DNS w samej przeglądarce, zaleca się przenieść ten ciężar na system operacyjny. Skonfigurowanie prywatnego DNS w ustawieniach Androida chroni ruch globalnie, dla wszystkich aplikacji na urządzeniu.

**Control D** to kanadyjska usługa DNS od twórców Windscribe, która oferuje darmowe resolvery publiczne bez konieczności zakładania konta. W darmowym tierze dostępne są gotowe presety filtrowania:

- **Control D (Ads & Tracking)** — `p2.freedns.controld.com` — blokuje reklamy, trackery i malware. Darmowy resolver nie przechowuje logów zapytań ani adresów IP.
- **Quad9** (`dns.quad9.net`) — maksymalna prywatność i ochrona przed malware. Szwajcarska fundacja non-profit, która nie loguje adresów IP. Nie filtruje reklam ani trackerów.
- **AdGuard DNS** (`dns.adguard-dns.com`) — blokowanie reklam, trackerów i złośliwych domen. Dobra opcja, jeśli zależy Ci na filtrowaniu treści.
- **NextDNS** — zaawansowana, w pełni konfigurowalna zapora (wymaga założenia konta). Pozwala na wybór własnych list filtrów i polityk dla różnych kategorii. Wsparcie projektu pozostawia jednak w ostatnim czasie wiele do życzenia.

Więcej o dostępnych presetach Control D znajdziesz na [controld.com/free-dns](https://controld.com/free-dns).

## Nota: twarde utwardzenie poza aplikacją

Powyższe zestawienie to fundament oparty wyłącznie na ustawieniach wewnątrz aplikacji. Dla zaawansowanych modeli zagrożeń istnieją metody pozwalające na głębsze utwardzenie przeglądarki. Wykorzystanie polis korporacyjnych (MDM / profil roboczy) pozwala wymusić wieloprocesową izolację witryn na poziomie silnika oraz zablokować opcje na stałe, uniemożliwiając przeglądarce ich reset w przypadku przyszłych aktualizacji.
