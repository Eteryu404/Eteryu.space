---
title: "Jak zainstalować Pixel Camera na GrapheneOS bez usług Google"
description: "Instrukcja instalacji aparatu Pixel Camera na GrapheneOS, z pełnym odcięciem od sieci i integracją z zewnętrzną galerią przez Gcam Services Provider."
icon: lucide/camera
---

Domyślny aparat w GrapheneOS (Secure Camera) jest w porządku, ale nie wykorzystuje w pełni możliwości układu Tensor. Pixel Camera od Google robi wyraźnie lepsze zdjęcia, zwłaszcza w trybie nocnym, ale standardowo wymaga usług Google Play i łączy się z siecią.

Ten poradnik pokazuje, jak zainstalować Pixel Camera na GrapheneOS bez wpuszczania usług Google do głównego profilu i bez oddawania aplikacji dostępu do sieci.

## Dlaczego warto to zrobić

| Cecha | Aparat GrapheneOS (Secure Camera) | Pixel Camera (Offline) |
| :--- | :--- | :--- |
| **Jakość zdjęć i tryb nocny** | Przeciętna. Nie wykorzystuje w pełni układu Tensor i zaawansowanych algorytmów Google. | **Rewelacyjna.** Pełne wsparcie procesora, fenomenalny tryb nocny (Night Sight) i HDR+. |
| **Prywatność (Out-of-the-box)** | **Absolutna.** Z założenia pozbawiona dostępu do sieci (`Network`) i jakiejkolwiek telemetrii. | Wymaga ręcznego odcięcia od sieci (**`Network Permission`**), by powstrzymać telemetrię. |
| **Integracja z galerią** | Bezproblemowa, korzysta z domyślnej galerii systemowej. | Wymaga instalacji mostka (`Gcam Services Provider`), by płynnie połączyć się z zewnętrzną galerią (np. Ente). |

## 1. Instalacja Pixel Camera

Kluczowa sprawa to aplikacja działająca bez usług Google Play w głównym profilu. Nie ma w internecie gotowego pliku instalacyjnego z w pełni zaufanego źródła, więc najlepszym wyjściem jest skorzystanie z `Aurora Store`. Nie polecam tego sklepu do codziennego użytku, ale w tym konkretnym przypadku jest to świadomy kompromis.

Co ważne, **nie musisz już szukać starszych wersji aplikacji po forach**. Jeszcze do niedawna Pixel Camera od wersji 10 wymuszała obecność usług Google Play z powodu braku dostępu do systemowej czcionki, co powodowało jej natychmiastowe zamykanie się.

**Dlaczego najnowsze wersje znów działają?**

Zespół GrapheneOS zaimplementował na poziomie systemu specjalną zaślepkę (ang. *shim*), która emuluje zachowanie usługi ładowania czcionek od Google. System skutecznie „oszukuje" aplikację, dostarczając jej to, czego wymaga, bez konieczności faktycznej instalacji usług Google Play. W efekcie najnowsze wersje Pixel Camera znów działają stabilnie prosto z pudełka.

> **Jak to zrobić:**
>
> - Pobierz sklep `Aurora Store` (podczas instalacji wybierz standardową paczkę, zazwyczaj pierwszą z brzegu, bez dopisków „hw" czy „preload").
> - Wyszukaj aplikację `Pixel Camera` i zainstaluj ją. Aurora Store sama dobierze najnowszą, kompatybilną z Twoim modelem telefonu wersję.
> - Aplikację `Aurora Store` od razu odinstaluj, jeśli nie korzystasz z niej na co dzień.

!!! warning "Aktualizacja ze starszych wersji"
    Jeśli masz zainstalowaną starszą wersję 9.x (build 68469120), **całkowicie ją odinstaluj** przed instalacją nowej. Przeskok na wersje z linii 10+ to spora zmiana i pozostawienie starych plików w pamięci podręcznej może powodować błędy. Najlepiej zainstalować nową wersję na czysto.

## 2. Kluczowe ustawienia po instalacji

Ostatni etap to nałożenie na aparat trzech restrykcji. Dostęp do sieci możesz zablokować już w samym oknie instalatora, natomiast po resztę musisz wejść w ustawienia nowo zainstalowanej aplikacji. Pamiętaj, by ustawić je ponownie, jeśli instalowałeś aparat na czysto.

- **`Network Permission`** (Dostęp do sieci) — w GrapheneOS przełącznik ten pojawia się już podczas instalacji i warto go od razu odznaczyć. Jeśli tego nie zrobiłeś, permanentnie odbierz to uprawnienie w ustawieniach. Aplikacja będzie całkowicie odcięta od internetu, a telemetria Google nie ma jak opuścić urządzenia.
- **`Storage Scopes`** (Zakresy pamięci) — zamiast dawać aplikacji Google pełny dostęp do wszystkich Twoich plików, uruchom tę funkcję GrapheneOS. Dzięki niej aparat uważa, że ma dostęp do pamięci (więc normalnie zapisuje zdjęcia), ale w rzeczywistości widzi tylko i wyłącznie własny folder. Jest całkowicie „ślepy" na resztę zawartości dysku.
- **`Allow background usage`** (Działanie w tle) — wyłącz tę opcję. Aparat nie ma żadnego powodu, by pracować w pamięci RAM, gdy z niego nie korzystasz. To prosty nawyk, który oszczędza baterię i zasoby telefonu.

## 3. Integracja z zewnętrzną galerią

Oryginalne wersje Pixel Camera domyślnie do podglądu zdjęć używają usługi Google Photos. Jeśli Twoją główną galerią jest np. `Ente Photos`, potrzebujesz mostka, który połączy aparat z zewnętrzną galerią.

Rozwiązaniem jest `Gcam Services Provider` w wariancie `photosonly` — open source'owy mostek autorstwa lukaspieper, dzięki któremu aparat działa stabilnie offline i płynnie współpracuje z zewnętrzną galerią.

- Wejdź na GitHub do sekcji wydań (releases) repozytorium: [lukaspieper / Gcam-Services-Provider](https://github.com/lukaspieper/Gcam-Services-Provider).
- Wybierz wariant `photos only`. Możesz go instalować i aktualizować wygodnie przez aplikację `Obtainium`.
- Bezpośredni link do pliku: [app-photosonly-release.apk](https://github.com/lukaspieper/Gcam-Services-Provider/releases/download/v1.6.1/app-photosonly-release.apk)

## Podsumowanie

Ten zestaw pozwala cieszyć się świetną jakością zdjęć oraz bezproblemową współpracą z wybraną galerią. To rozwiązanie nie tylko dla Pixela 8, ale dla każdego urządzenia z GrapheneOS, na którym nie chcesz instalować usług Google w głównym profilu.
