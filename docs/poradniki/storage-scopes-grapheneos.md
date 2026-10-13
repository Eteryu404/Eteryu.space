---
title: "Storage Scopes w GrapheneOS: jak odciąć aplikacje od Twoich plików"
description: "GrapheneOS potrafi okłamać aplikację, że ma pełny dostęp do pamięci, a w rzeczywistości pokazać jej tylko wybrane foldery. Instrukcja konfiguracji Storage Scopes."
icon: lucide/folder-lock
---

W standardowym Androidzie model uprawnień do pamięci bywa problematyczny. Nowsze wersje systemu (od Androida 13) oferują wybiórczy dostęp do zdjęć, ale wiele aplikacji — komunikatory, menedżery plików, starsze programy — nadal stosuje szantaż: żądają szerokiego dostępu, a jeśli odmówisz, zawieszają się albo odmawiają działania. Deweloper nie przewidział innej ścieżki.

Zmuszeni klikamy „zezwól na wszystko". W ten sposób oddajemy wgląd w prywatne zdjęcia z wakacji, zrzuty ekranu z aplikacji bankowych, dokumenty i memy. Wszystko, co znajduje się w pamięci telefonu, staje się dostępne dla aplikacji.

GrapheneOS rozwiązuje ten problem przez sprytne oszustwo systemowe.

## Problem: pełny dostęp albo nic

W standardowym Androidzie aplikacja, która nie dostanie pełnego dostępu do plików, często nie działa poprawnie. System oferuje bezpieczniejsze rozwiązania — mechanizm `SAF (Storage Access Framework)` oraz nowszy `Photo Picker` — które pozwalają wywołać systemowe okno wyboru pliku bez dawania aplikacji uprawnień do całej pamięci. Ale to wymaga dobrej woli dewelopera. Wiele aplikacji (w tym najpopularniejsze komunikatory) celowo ignoruje te standardy i wymusza szeroki dostęp pod pretekstem wygody.

## Rozwiązanie: Storage Scopes

Dla takich opornych aplikacji GrapheneOS stworzył `Storage Scopes` — mechanizm, który rozwiązuje sprawę siłowo, bez pytania dewelopera o zdanie.

Zamiast blokować aplikację i ryzykować jej awarię, system GrapheneOS kłamie. Zwraca aplikacji informację zwrotną potwierdzającą rzekome otrzymanie pełnego dostępu do pamięci. Aplikacja jest zadowolona i działa stabilnie. W rzeczywistości system izoluje ją w wirtualnej piaskownicy: aplikacja widzi wyłącznie te foldery i pliki, które Ty jej ręcznie wskażesz. Cała reszta pamięci telefonu po prostu dla niej nie istnieje.

| Cecha | Standardowy Android | GrapheneOS (Storage Scopes) |
| :--- | :--- | :--- |
| **Brak zgody na pełny dostęp** | Często powoduje zawieszanie się lub odmowę uruchomienia aplikacji. | Aplikacja działa stabilnie, bo uważa, że otrzymała pełne uprawnienia. |
| **Widoczność plików** | Aplikacja ma prawo skanować szerszy zakres pamięci. | Aplikacja widzi **tylko** wskazany przez Ciebie folder lub plik. |
| **Prywatność** | Umiarkowana, zależna od uczciwości twórców aplikacji. | **Absolutna.** Kod aplikacji jest ślepy na resztę systemu. |

## Przykłady zastosowań

**Aparat.** Weźmy `Pixel Camera`. Zależy nam na rewelacyjnej jakości zdjęć i algorytmach Google, ale nie chcemy, żeby kod tej korporacji miał wgląd w prywatną galerię. Włączamy `Storage Scopes` dla tej aplikacji i — co ciekawe — nie wskazujemy jej żadnego folderu. Aplikacje w Androidzie nie potrzebują specjalnych uprawnień, żeby **zapisywać** tworzone przez siebie pliki w standardowych folderach publicznych (np. `DCIM`). Aparat zrobi zdjęcie i zapisze je bez problemu, ale dzięki systemowemu kłamstwu pozostanie całkowicie ślepy na starsze fotografie czy zrzuty ekranu.

**Komunikatory.** WhatsApp, Discord i tym podobne potrafią żądać dostępu do całej galerii. Zamiast na to pozwalać, przyznaj im w `Storage Scopes` dostęp tylko do jednego pustego folderu, do którego sam będziesz kopiować pliki przeznaczone do wysłania.

## Konfiguracja krok po kroku

Kiedy nowo zainstalowana aplikacja w GrapheneOS po raz pierwszy prosi o dostęp do plików, w systemowym oknie z zapytaniem na samym dole znajdziesz bezpośredni przycisk **`Storage scopes`**. To najszybsza metoda.

Jeśli chcesz zarządzać tym ręcznie albo zmodyfikować ustawienia po czasie:

1. Wejdź w ustawienia danej aplikacji (Informacje o aplikacji).
2. Wybierz zakładkę z uprawnieniami, a następnie pozycję `Zdjęcia i filmy` lub `Pliki i multimedia`.
3. Zamiast opcji zezwalającej na pełny dostęp, wybierz na samym dole **`Setup Storage Scopes`**.
4. Kliknij **`Add folder`** lub **`Add file`**.
5. Wskaż w systemowym menedżerze konkretne miejsce, z którego aplikacja ma prawo czytać dane.

Możesz dodać kilka folderów naraz. W każdej chwili możesz wrócić do tych ustawień, żeby zmodyfikować zakres przydzielonych zasobów.

!!! warning "Utrata dostępu po reinstalacji"
    Jeśli odinstalujesz aplikację używającą Storage Scopes, a potem zainstalujesz ją ponownie, system potraktuje ją jako zupełnie nowy program. Straci dostęp do plików, które wcześniej sama stworzyła. Aby go przywrócić, musisz ręcznie dodać odpowiedni folder w ustawieniach.

## Podsumowanie

Prywatność nie musi oznaczać rezygnacji z wygody. Mechanizm `Storage Scopes` pokazuje, że można używać popularnych aplikacji o zamkniętym kodzie w sposób kontrolowany i bezpieczny — bez proszenia dewelopera o zgodę i bez ryzykowania awarii aplikacji.
