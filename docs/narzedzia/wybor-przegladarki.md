---
title: Wybór Przeglądarki
description: Kryteria wyboru przeglądarki pod kątem bezpieczeństwa architektury. Dlaczego Chrome, Vanadium i Brave wygrywają z alternatywami opartymi na Firefoksie.
icon: lucide/globe-lock
---

# Architektura przeglądarek i kryteria wyboru

!!! tip "Rekomendacje końcowe"
    *   **:material-microsoft-windows: Windows** — Google Chrome
    *   **:material-apple: macOS** — Google Chrome
    *   **:material-android: Android** — Google Chrome lub Brave (Brave zalecany ze względu na tryb JITless V8 pomimo szerszej powierzchni ataku).
        *   **:simple-grapheneos: GrapheneOS** — Vanadium
    *   **:material-apple: iOS** — Safari
    *   **:material-linux: Linux** — Google Chrome lub Brave Origin
        *   **:material-fedora: Oparte na Fedorze** — [Trivalent](https://github.com/secureblue/Trivalent)
        *   **:material-arch: Arch Linux** — [Oficjalny pakiet Chromium z repozytorium](https://archlinux.org/packages/extra/x86_64/chromium/)
        *   **:material-nix: NixOS** — [Pakiet Chromium z Nixpkgs](https://github.com/NixOS/nixpkgs/tree/master/pkgs/applications/networking/browsers/chromium)

Wybór odpowiedniej przeglądarki to najistotniejsza decyzja w architekturze osobistego bezpieczeństwa. Poniższy materiał definiuje rygorystyczne kryteria techniczne na podstawie których należy oceniać oprogramowanie tego typu oraz wyjaśnia powody klasyfikacji poszczególnych silników.

## Kryteria bazowe

Najbardziej krytycznym elementem bezpieczeństwa przeglądarki jest cykl aktualizacji. Wszelkie inne mechanizmy ochronne tracą znaczenie jeśli oprogramowanie jest aktualizowane rzadziej niż co kilka tygodni. Podatności kumulują się z każdym dniem. Dla kontekstu stabilne wydania Chromium pojawiają się średnio co tydzień lub dwa zazwyczaj łatając przynajmniej jedną podatność o wysokim priorytecie. Dwa miesiące bez aktualizacji to ekspozycja na wiele krytycznych błędów. Żadne utwardzanie nie skompensuje tej luki.

Drugim kluczowym czynnikiem jest jakość procesu budowania i weryfikacja czy dany wariant oferuje przynajmniej te same mechanizmy obronne co czyste Chromium. Przykładem jest weryfikacja integralności przepływu sterowania (CFI). Choć jest to domyślny standard w Chromium wiele wariantów lub dystrybucji Linuksa celowo wyłącza ten mechanizm podczas kompilacji co stanowi drastyczną regresję bezpieczeństwa.

Trzeci aspekt to funkcje dodatkowe oraz bezpieczne ustawienia domyślne. Obejmuje to możliwość rygorystycznej kontroli nad ryzykownymi technologiami takimi jak telemetria czy WebAssembly. Z perspektywy bezpieczeństwa architektury fakt czy przeglądarka jest zamkniętoźródłowa czy otwartoźródłowa ma marginalne znaczenie. Otwarty kod jest preferowany ze względu na transparentność jednak nie jest czynnikiem decydującym o kompromisie w kwestii bezpieczeństwa izolacji procesów.

## Profilowanie i teatr prywatności

Ochrona przed profilowaniem jest niezwykle trudna do poprawnego wdrożenia. Większość wbudowanych mechanizmów losowania danych jedynie wyróżnia użytkownika na tle populacji tworząc jeszcze bardziej unikalny profil cyfrowy. 

!!! warning "Zagrożenie architektoniczne"
    Popularna praktyka korzystania z wielu przeglądarek w celu separacji tożsamości to wyłącznie teatr prywatności. Zwiększa to jedynie powierzchnię ataku i wymusza zaufanie do wielu różnych architektur. Znacznie bezpieczniejszym i skuteczniejszym podejściem jest korzystanie z wbudowanego menedżera profili w ramach jednej sprawdzonej przeglądarki.

Skuteczna ochrona przed profilowaniem wymaga dedykowanych rozwiązań takich jak Tor Browser izolowany w maszynie wirtualnej.

## Blokowanie treści i reklam

Skuteczne filtrowanie zapytań można zrealizować na trzy główne sposoby z których każdy niesie inny poziom kompromisu między bezpieczeństwem a skutecznością.

*   **Rozszerzenia przeglądarki:** Tradycyjne rozszerzenia w standardzie Manifest V2 stanowią poważne zagrożenie dla izolacji witryn ponieważ posiadają pełny dostęp do wszystkich stron i ich zawartości. Rozwiązaniem akceptowalnym architektonicznie jest standard Manifest V3. Rozszerzenia takie jak uBlock Origin Lite w trybie podstawowym blokują niechciane treści bez żądania uprawnień do odczytu danych co znacznie redukuje ryzyko. Należy pamiętać że zdalnie aktualizowane listy filtrów w starych rozszerzeniach mogą wykonywać arbitralny kod w postaci skryptów co stanowi bezpośrednie zagrożenie.
*   **Rozwiązania natywne:** Najbezpieczniejszym podejściem jest użycie wbudowanego filtra zasobów silnika Chromium wykorzystywanego przez Vanadium oraz Trivalent. Metoda ta zachowuje pełne bezpieczeństwo ponieważ nie dodaje żadnego obcego kodu do przeglądarki. Z kolei integracja zewnętrznych silników filtrujących tak jak ma to miejsce w Brave zwiększa ogólną powierzchnię ataku.
*   **Filtrowanie sieciowe i DNS:** Metoda ta jest bezapelacyjnie najbezpieczniejsza ale oferuje najmniejszą precyzję. Pozwala wyłącznie na blokowanie całych domen ignorując precyzyjne ścieżki wewnątrz witryn. Zawsze zaleca się stosowanie szyfrowanego protokołu DNS z filtrowaniem jako bazowej warstwy obronnej ponieważ nie wpływa to negatywnie na wydajność urządzenia.
    
    !!! danger "Krytyczne ryzyko bezpieczeństwa"
        Należy bezwzględnie unikać lokalnych systemów inspekcji HTTPS które przechwytują szyfrowany ruch za pomocą własnych certyfikatów. Rozwiązania te łamią podstawową strukturę szyfrowania i wymuszają zaufanie względem zewnętrznego oprogramowania.

## Dlaczego te konkretne narzędzia

Nasze zestawienie ogranicza się do zaledwie kilku projektów. Ignorujemy popularne narzędzia marketingowo skupione na prywatności jeśli ich architektura fundamentalnie ustępuje liderom jak ma to miejsce w przypadku środowisk opartych na Firefoksie które cierpią na słabą izolację procesów.

### :material-google-chrome: Google Chrome
Punkt odniesienia dla wszystkich innych projektów. Chrome dysponuje absolutnie najszybszym cyklem aktualizacji oraz najbardziej dopracowaną architekturą izolacji procesów. Jest to oprogramowanie oferujące najwyższy poziom odporności na eksploity. Zamknięty kod źródłowy nie wpływa negatywnie na jego bezpieczeństwo jednak przeglądarka ta wymaga rygorystycznej konfiguracji ręcznej w celu wyłączenia wbudowanej telemetrii.

### :material-shield-search: Vanadium
Prawdopodobnie najbezpieczniejsza przeglądarka na rynku dostępna wyłącznie dla środowiska GrapheneOS. Oferuje ekstremalne utwardzenie kodu oraz zaawansowaną ochronę pamięci deklasując standardowe rozwiązania mobilne. Cykl aktualizacji jest wysoce rygorystyczny i spójny z wydaniami Chromium.

### :fontawesome-brands-brave: Brave
Rozwiązanie kompromisowe zalecane głównie dla systemu Android jako alternatywa dla użytkowników pozbawionych dostępu do Vanadium. Jej główną przewagą techniczną na platformie mobilnej jest flaga pozwalająca na wyłączenie kompilatora JIT co drastycznie ucina powierzchnię ataku. Należy jednak pamiętać że Brave implementuje wiele zbędnych funkcji co niepotrzebnie komplikuje architekturę. W środowiskach desktopowych Chrome zawsze pozostaje lepszym wyborem ze względu na czystość kodu.
