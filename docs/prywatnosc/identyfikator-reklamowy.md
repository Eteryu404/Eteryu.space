---
title: Identyfikator Reklamowy
description: Jak trwale usunąć identyfikator reklamowy (Ad ID / IDFA) w Androidzie i iOS, żeby odciąć systemową telemetrię i utrudnić profilowanie behawioralne.
icon: lucide/barcode
---

# Identyfikator reklamowy

!!! abstract "Cel artykułu"
    Trwałe usunięcie globalnego identyfikatora śledzącego (Advertising ID) na poziomie systemu operacyjnego. Dokument definiuje procedurę odcięcia natywnej telemetrii, zapobiegając masowemu profilowaniu behawioralnemu przez sieci reklamowe i brokerów danych w środowiskach Android oraz iOS.

## Architektura profilowania (Czym jest Ad ID?)

Zarówno system Android, jak i iOS domyślnie generują i przypisują do urządzenia unikalny ciąg alfanumeryczny – tzw. identyfikator reklamowy (Ad ID / IDFA w środowisku Apple). Identyfikator ten istnieje w jednym głównym celu: aby pomóc firmom w śledzeniu użytkownika. Pełni on funkcję systemowego, cyfrowego tatuażu.

Aplikacje teoretycznie działające w środowisku izolowanym (tzw. sandbox) wykorzystują ten globalny identyfikator do oznaczania przesyłanych pakietów. Identyfikator reklamowy pozwala modułom śledzącym na łączenie danych z różnych źródeł w jedną tożsamość. Co więcej, ponieważ każda aplikacja i skrypt widzi ten sam identyfikator, umożliwia to brokerom danych wymianę informacji o Tobie. W praktyce broker A może kupić dane od brokera B, a następnie użyć identyfikatora reklamowego, aby połączyć te dwa zbiory danych w jeden kompleksowy profil.

!!! danger "Mit pseudonimowości"
    Uczestnicy rynku handlu danymi często argumentują, że identyfikator reklamowy jest anonimowy lub pseudonimowy, co ma sugerować, że nie stanowi poważnego zagrożenia dla prywatności. W praktyce jest to nieprawda.
    
    * Identyfikator ten jest powszechnie używany do zbierania danych, które w oczywisty sposób identyfikują osobę, takich jak bardzo szczegółowe dane lokalizacyjne.
    * Jeśli algorytm widzi, gdzie dana osoba pracuje, śpi, uczy się, spędza czas wolny i szuka opieki medycznej, adres e-mail nie jest już potrzebny do jej zidentyfikowania.
    * Istnieje cała branża, której celem jest pomoc firmom śledzącym w łączeniu identyfikatorów reklamowych z bardziej bezpośrednimi danymi identyfikacyjnymi, takimi jak adresy e-mail czy numery telefonów.

Wyłączenie tego identyfikatora znacząco utrudnia większości reklamodawców i brokerów danych śledzenie Twojej aktywności, co nie tylko chroni prywatność, ale też sprawia, że przemysł reklamy opartej na inwigilacji staje się mniej rentowny. Dla zobrazowania skali zjawiska: sama firma Facebook przyznała, że wprowadzenie przez Apple funkcji App Tracking Transparency (która blokuje dostęp do IDFA) miało obniżyć przychody firmy w 2022 roku o około 10 miliardów dolarów.

Odcięcie dostępu do tego identyfikatora jest zatem absolutnym priorytetem przed wdrożeniem dalszych warstw prywatności.

## Procedura neutralizacji

Wybierz platformę operacyjną, na której aktualnie pracujesz, aby wyświetlić odpowiednią procedurę:

=== "Android"

    Począwszy od systemu Android 12, Google umożliwiło użytkownikom całkowite usunięcie identyfikatora reklamowego. W celu jego trwałego usunięcia należy wykonać poniższe kroki operacyjne:

    1. Otwórz główne **Ustawienia** urządzenia.
    2. Przejdź do sekcji **Prywatność**, a następnie wybierz **Reklamy** (lub w niektórych nakładkach: *Google* -> *Reklamy*).
    3. Wybierz opcję **Usuń identyfikator reklamowy** i potwierdź wykonanie procedury na kolejnym ekranie. Zapobiegnie to dostępowi do niego jakiejkolwiek aplikacji w przyszłości.

    !!! info "Starsze wersje systemu (Android 11 i niżej)"
        Na starszych urządzeniach opcja całkowitego usunięcia może nie być dostępna. Należy wtedy wybrać w tym samym menu opcję nakazującą systemowi zablokowanie personalizacji reklam, co spowoduje wyzerowanie identyfikatora i wysłanie sygnału o braku zgody na śledzenie.

=== "iOS (Apple)"

    Firma Apple wymaga od aplikacji uzyskania zgody, zanim będą one mogły uzyskać dostęp do IDFA. Konfigurację tę należy uszczelnić na poziomie globalnym, aby system zablokował aplikacjom samą możliwość wyświetlania zapytań o śledzenie.

    **Krok 1: Globalna blokada śledzenia przez aplikacje (IDFA)**
    
    1. Otwórz **Ustawienia** systemu iOS.
    2. Przejdź do sekcji **Prywatność i ochrona**, a następnie wybierz **Śledzenie**.
    3. Dezaktywuj opcję **Pozwalaj aplikacjom żądać możliwości śledzenia**.
    4. Zapobiegnie to pytaniom o śledzenie w przyszłości, a jeśli aplikacje otrzymały taką zgodę w przeszłości, system zaproponuje nakazanie im zaprzestania śledzenia.

    **Krok 2: Ograniczenie natywnego profilowania Apple**
    
    Apple posiada własny system reklamy ukierunkowanej, oddzielony od śledzenia przez podmioty trzecie, które firma umożliwia za pomocą IDFA. Aby go wyłączyć:
    
    1. Wróć do menu **Prywatność i ochrona**.
    2. Zjedź na sam dół i wybierz **Reklamy Apple**.
    3. Ustaw przełącznik **Spersonalizowane reklamy** na pozycję wyłączoną, aby dezaktywować targetowanie reklam przez Apple.
