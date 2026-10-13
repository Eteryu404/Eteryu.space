---
title: Identyfikator Reklamowy
description: Czym jest identyfikator reklamowy (Ad ID / IDFA), dlaczego umożliwia masowe profilowanie behawioralne i jak działa rynek handlu danymi.
icon: lucide/barcode
---

# Identyfikator reklamowy

!!! abstract "Cel artykułu"
    Wyjaśnienie, czym jest globalny identyfikator śledzący (Advertising ID) i dlaczego jego obecność w systemie operacyjnym umożliwia masowe profilowanie behawioralne przez sieci reklamowe i brokerów danych. Instrukcje techniczne usunięcia identyfikatora znajdują się w poradniku [Jak usunąć identyfikator reklamowy](../poradniki/cyfrowa-higiena-przerwa-na-kawe.md).

## Architektura profilowania

Zarówno system Android, jak i iOS domyślnie generują i przypisują do urządzenia unikalny ciąg alfanumeryczny — tzw. identyfikator reklamowy (Ad ID / IDFA w środowisku Apple). Identyfikator ten istnieje w jednym głównym celu: aby pomóc firmom w śledzeniu użytkownika. Pełni funkcję systemowego, cyfrowego tatuażu.

Aplikacje teoretycznie działające w środowisku izolowanym (tzw. sandbox) wykorzystują ten globalny identyfikator do oznaczania przesyłanych pakietów. Identyfikator reklamowy pozwala modułom śledzącym na łączenie danych z różnych źródeł w jedną tożsamość. Co więcej, ponieważ każda aplikacja i skrypt widzi ten sam identyfikator, brokerzy danych mogą wymieniać się informacjami o Tobie. W praktyce broker A może kupić dane od brokera B, a następnie użyć identyfikatora reklamowego, aby połączyć te dwa zbiory danych w jeden kompleksowy profil.

!!! danger "Mit pseudonimowości"
    Uczestnicy rynku handlu danymi często argumentują, że identyfikator reklamowy jest anonimowy lub pseudonimowy, co ma sugerować, że nie stanowi poważnego zagrożenia dla prywatności. W praktyce to nieprawda.

    - Identyfikator jest powszechnie używany do zbierania danych, które w oczywisty sposób identyfikują osobę, takich jak bardzo szczegółowe dane lokalizacyjne.
    - Jeśli algorytm widzi, gdzie dana osoba pracuje, śpi, uczy się, spędza czas wolny i szuka opieki medycznej, adres e-mail nie jest już potrzebny do jej zidentyfikowania.
    - Istnieje cała branża, której celem jest pomoc firmom śledzącym w łączeniu identyfikatorów reklamowych z bardziej bezpośrednimi danymi identyfikacyjnymi, takimi jak adresy e-mail czy numery telefonów.

## Skala zjawiska

Wyłączenie tego identyfikatora znacząco utrudnia większości reklamodawców i brokerów danych śledzenie Twojej aktywności. Chroni to prywatność, ale też sprawia, że przemysł reklamy opartej na inwigilacji staje się mniej rentowny.

Dla zobrazowania skali: sama firma Facebook przyznała, że wprowadzenie przez Apple funkcji App Tracking Transparency (która blokuje dostęp do IDFA) miało obniżyć przychody firmy w 2022 roku o około 10 miliardów dolarów.

Odcięcie dostępu do tego identyfikatora jest zatem absolutnym priorytetem przed wdrożeniem dalszych warstw prywatności.

## Jak usunąć identyfikator?

Instrukcje techniczne dla Androida i iOS, z uwzględnieniem starszych wersji systemu oraz natywnego profilowania Apple, znajdziesz w poradniku [Cyfrowa higiena podczas przerwy na kawę](../poradniki/cyfrowa-higiena-przerwa-na-kawe.md).
