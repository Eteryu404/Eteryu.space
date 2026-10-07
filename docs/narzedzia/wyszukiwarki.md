---
title: Wybór Wyszukiwarki
description: Prywatne wyszukiwarki, które nie budują profilu reklamowego na podstawie Twoich zapytań. Porównanie indeksów, jurysdykcji i modeli biznesowych.
icon: lucide/search
---

# Wybór wyszukiwarki

Wyszukiwarka to jedno z pierwszych miejsc, w których ujawniamy nasze intencje. Każde zapytanie to mały fragment układanki, z której powstaje profil. Poniżej znajdziesz wyszukiwarki, które nie budują profilu reklamowego na podstawie Twoich zapytań. Wybór należy do Ciebie – każda z nich ma inne zalety i kompromisy.

## Porównanie

| Wyszukiwarka | Indeks | Jurysdykcja | Logi IP | Logi zapytań | Koszt |
|---|---|---|---|---|---|
| **Brave Search** | Własny | USA | Nie | Nie | Darmowy |
| **DuckDuckGo** | Bing | USA | Nie | Nie | Darmowy |
| **Startpage** | Google + Bing | Holandia | Nie (anonimizacja) | Nie | Darmowy |
| **Qwant** | Własny (EUSP/Staan) | Francja | Nie | Nie | Darmowy |
| **Mojeek** | Własny | UK | Nie (zastępowany kodem kraju) | Nie | Darmowy |
| **Kagi** | Własny + inne | USA | Nie | Usuwane po 7 dniach | Płatny |
| **SearXNG** | Meta | Self-hosted | Zależne od instancji | Zależne od instancji | Darmowy |

## Opisy

### Brave Search
Własny indeks (ponad 40 miliardów stron), niezależny od Google i Bing. Domyślna wyszukiwarka w Brave Browser. Firma podkreśla, że nie przechowuje danych, które mogłyby łączyć zapytania z użytkownikiem, urządzeniem lub adresem IP. Wymaga wyłączenia anonimowych metryk w ustawieniach.

### DuckDuckGo
Najbardziej mainstreamowa prywatna wyszukiwarka. Korzysta głównie z wyników Bing, ale nie przekazuje Bingowi Twoich zapytań w sposób, który mógłby posłużyć do ich powiązania z Twoją tożsamością. Niezależny audyt bezpieczeństwa (Securitum) potwierdził, że DuckDuckGo nie loguje aktywności użytkowników ani metadanych połączenia. Ma wersję bez AI (`noai.duckduckgo.com`) i wersje bez JavaScript.

### Startpage
Proxy do Google i Bing. Otrzymujesz wyniki Google, ale zapytanie jest anonimizowane – Google i Microsoft widzą tylko Startpage, nie Ciebie. Siedziba w Holandii (UE), ale firma należy do Surfboard Holding B.V., która jest częścią System1, amerykańskiej spółki publicznej. Startpage zachowuje jednak niezależność operacyjną w kwestiach prywatności. Ma funkcję „Anonymous View", która standaryzuje aktywność użytkownika i ukrywa Twój adres IP przed odwiedzanymi stronami.

### Qwant
Francuska wyszukiwarka działająca od 2013 roku. Nie profiluje użytkowników i nie sprzedaje danych. Od 2024 roku współtworzy europejski indeks we współpracy z Ecosia w ramach joint venture European Search Perspective (EUSP). Indeks nosi nazwę Staan i ma uniezależnić Europę od Google i Bing. W lipcu 2026 roku EUSP uruchomiło własny indeks dla rynku niemieckiego (ok. miliarda stron), po wcześniejszym wdrożeniu we Francji. Na początku 2026 roku Europejski Parlament wybrał Qwant jako domyślną wyszukiwarkę na swoich komputerach. W lutym 2025 roku francuski organ ochrony danych (CNIL) przypomniał Qwant o obowiązkach wynikających z RODO, uznając, że dane przekazywane do Microsoftu były pseudonimowe, a nie w pełni anonimowe.

### Mojeek
Brytyjska wyszukiwarka z własnym indeksem od 2006 roku. Mniejszy indeks niż Brave, ale w pełni niezależny. Firma podkreśla, że nie posiada żadnych informacji identyfikujących użytkownika – adresy IP są zastępowane dwuliterowym kodem kraju pochodzenia. Brak reklam opartych na profilowaniu.

### Kagi
Płatna wyszukiwarka ($5-10/miesiąc). Brak reklam, zaawansowane filtry (możliwość blokowania domen, „lenses"). Wymaga konta do rozliczenia – nie służy ono do profilowania reklamowego ani budowania profilu na podstawie zapytań. Kagi deklaruje, że nie loguje wyszukiwań ani nie wiąże ich z kontem; jedynym przechowywanym danym jest adres e-mail do odzyskiwania konta. Zapytania są anonimizowane i usuwane po 7 dniach.

### SearXNG
Open source, self-hosted metawyszukiwarka. Agreguje wyniki z wielu źródeł. Usuwa prywatne dane z zapytań kierowanych do wyszukiwarek zewnętrznych i nie przekazuje reklam ani treści śledzących. Wymaga własnej instancji lub zaufania do instancji publicznej – operator publicznej instancji może teoretycznie logować zapytania.

## Jak zmienić wyszukiwarkę

=== "Android"

    W większości przeglądarek: `Ustawienia` → `Wyszukiwarka` → wybierz z listy.

=== "iOS"

    W Safari: `Ustawienia` → `Safari` → `Wyszukiwarka`. W innych przeglądarkach: `Ustawienia` → `Wyszukiwarka`.

## Kryteria

Poniższe kryteria określają, co wyszukiwarka musi spełnić, żeby znaleźć się w tym zestawieniu. To próg kwalifikacji, a nie wymiary porównania – te znajdziesz w tabeli powyżej.

**Minimum:**

- Nie zbiera danych osobowych (PII) zgodnie z polityką prywatności.
- Nie wymaga zakładania konta.*

\*Wyjątek: narzędzia płatne (np. Kagi), gdzie konto jest niezbędne do rozliczenia, ale nie służy do profilowania reklamowego.

**Zalecane:**

- Oparta na otwartym kodzie źródłowym.
- Nie blokuje adresów IP węzłów wyjściowych Tor.
- Ma własny indeks (nie jest wyłącznie proxy do Google lub Bing).
