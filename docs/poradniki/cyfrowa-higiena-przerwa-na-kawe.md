---
title: "Szybkie zwycięstwa dla prywatności w 10 minut"
description: "Kilka prostych nawyków, które odcinają większość komercyjnego szpiegowania na telefonie: identyfikator reklamowy, cztery uprawnienia krytyczne i filtrowanie DNS."
icon: lucide/zap
---

Nasze smartfony bez przerwy nadają o tym, gdzie jesteśmy i co robimy. Dobra wiadomość: odcięcie większości komercyjnego szpiegowania nie wymaga bycia ekspertem od cyberbezpieczeństwa. To kwestia kilku prostych nawyków, które wdrożysz podczas krótkiej przerwy na kawę.

## 1. Usuń identyfikator reklamowy

Większość z nas nosi w kieszeni unikalny numer ukryty głęboko w systemie, tak zwany **identyfikator reklamowy**. To cyfrowy tatuaż, który pozwala firmom marketingowym i brokerom danych łączyć Twoje luźne ruchy w różnych aplikacjach w jeden spójny profil. Jeśli chcesz zrozumieć, dlaczego to realne zagrożenie, zajrzyj do sekcji [Identyfikator reklamowy](../prywatnosc/identyfikator-reklamowy.md) w Bazie Wiedzy.

=== "Android"

    Począwszy od Androida 12, Google umożliwiło całkowite usunięcie identyfikatora reklamowego.

    1. Otwórz główne **Ustawienia** telefonu i przejdź do sekcji **Prywatność** → **Reklamy** (w niektórych nakładkach: *Google* → *Reklamy*).
    2. Wybierz opcję **„Usuń identyfikator reklamowy"** i potwierdź wybór na kolejnym ekranie. Zapobiegnie to dostępowi do identyfikatora przez jakąkolwiek aplikację w przyszłości.

    !!! info "Starsze wersje systemu (Android 11 i niżej)"
        Na starszych urządzeniach opcja całkowitego usunięcia może nie być dostępna. Wybierz wtedy opcję blokującą personalizację reklam. Spowoduje to wyzerowanie identyfikatora i wysłanie sygnału o braku zgody na śledzenie.

    Jeśli ekran jest zupełnie pusty i widzisz tylko pojedynczy link informacyjny, to gratulacje. Oznacza to, że po wcześniejszym wyłączeniu personalizacji reklam na koncie Google system automatycznie wykasował identyfikator z urządzenia.

    ![Tak wygląda poprawnie wyczyszczony ekran reklamowy Google w systemie Android](https://i.postimg.cc/zG2m1BbS/Resized-Image-2026-06-24-13-43-21-9511.png)

=== "iOS (Apple)"

    Apple wymaga od aplikacji uzyskania zgody, zanim będą mogły uzyskać dostęp do IDFA. Konfigurację uszczelniamy na poziomie globalnym.

    **Krok 1: Globalna blokada śledzenia przez aplikacje (IDFA)**

    1. Otwórz **Ustawienia** systemu iOS.
    2. Przejdź do sekcji **Prywatność i ochrona**, a następnie wybierz **Śledzenie**.
    3. Dezaktywuj opcję **„Pozwalaj aplikacjom żądać możliwości śledzenia"**.
    4. Zapobiegnie to pytaniom o śledzenie w przyszłości. Jeśli aplikacje otrzymały zgodę w przeszłości, system zaproponuje nakazanie im zaprzestania śledzenia.

    **Krok 2: Ograniczenie natywnego profilowania Apple**

    Apple ma własny system reklamy ukierunkowanej, oddzielony od śledzenia przez podmioty trzecie. Aby go wyłączyć:

    1. Wróć do menu **Prywatność i ochrona**.
    2. Zjedź na sam dół i wybierz **Reklamy Apple**.
    3. Ustaw przełącznik **Spersonalizowane reklamy** na pozycję wyłączoną.

W obu przypadkach cel zostaje osiągnięty: dla przemysłu reklamowego stajesz się czystą kartą.

## 2. Wielka czwórka uprawnień

Zanim bezrefleksyjnie klikniesz „Zezwól" przy kolejnym wyskakującym okienku, zatrzymaj się na sekundę. Aby aplikacja mogła Cię skutecznie profilować, musi zebrać dane, działać po cichu, kiedy śpisz, i mieć jak wysłać te paczki na serwer brokerów.

### Lokalizacja to nie przymus

Aplikacje do zamawiania taksówek i pogodynki świetnie dadzą sobie radę bez GPS, wystarczy ręcznie wpisać adres lub nazwę miasta. Zamiast usług od Google czy Apple możesz postawić na rozwiązania lokalne i otwartoźródłowe, takie jak `Organic Maps` czy `OsmAnd`. Wgrywasz do nich pobrane wcześniej mapy i podróżujesz całkowicie offline. Jeśli inna aplikacja koniecznie domaga się lokalizacji, zawsze wybieraj opcję **przybliżoną** zamiast precyzyjnej.

### Ukryte radary (skanowanie Wi-Fi i Bluetooth)

Większość ludzi myśli, że jak wyłączy GPS, to jest niewidzialna. Nic bardziej mylnego. Telefony domyślnie przeczesują otoczenie w poszukiwaniu routerów i beaconów reklamowych, nawet gdy masz te moduły oficjalnie wyłączone. Brokerzy danych używają tych sygnałów, żeby wiedzieć, przy której półce sklepowej stoisz.

Wejdź w ustawienia lokalizacji, znajdź sekcję `Skanowanie Wi-Fi i Bluetooth` i wyłącz obie opcje.

### Odcięcie od sieci

Jeśli aplikacja (czytnik PDF, kalkulator, gra jednoosobowa) działa w stu procentach lokalnie, zablokuj jej dostęp do internetu komórkowego i Wi-Fi. Choćby zebrała tonę statystyk wewnątrz telefonu, bez dostępu do sieci nie ma jak wysłać ich w świat.

!!! tip "Blokada sieci na czystym Androidzie"
    Nakładki takie jak `One UI` (Samsung) czy `HyperOS` (Xiaomi) mają wbudowane opcje blokowania sieci w ustawieniach aplikacji. Jeśli używasz czystego Androida, np. na Pixelu, możesz użyć prostej i bezpiecznej aplikacji typu firewall, na przykład `NetGuard`.

### Koniec z pracą na trzy zmiany

Wiele aplikacji żyje własnym życiem, kiedy z nich nie korzystasz. Wejdź w ustawienia aplikacji (lub baterii) i dla wszystkiego, co nie musi wysyłać natychmiastowych powiadomień, wyłącz opcję **„Zezwalaj na działanie w tle"** (`Allow background usage`). Telefon nie tylko przestanie nadawać za Twoimi plecami, ale też podziękuje dłuższym czasem pracy na jednym ładowaniu.

## 3. Postaw systemową tarczę na trackery

Wszystko, co mimo powyższych blokad spróbuje wysłać zapytanie z telefonu, można przefiltrować w locie, zanim dotrze do serwerów szpiegujących. Masz do wyboru dwie proste drogi.

- **Prywatny DNS.** Wbudowana w każdy nowoczesny telefon funkcja. Wchodzisz w ustawienia sieciowe, znajdujesz opcję `Prywatny DNS` i wpisujesz tam darmowy adres filtrujący, np. od `NextDNS` lub `AdGuard`. Od tej sekundy system sam blokuje zapytania do znanych sieci reklamowych. Szczegóły znajdziesz w poradniku [Jak skonfigurować prywatny DNS](prywatny-dns-w-5-minut.m).
- **VPN z filtrem.** Jeśli zależy Ci nie tylko na blokowaniu trackerów, ale też na zamaskowaniu adresu IP i zaszyfrowaniu ruchu, użyj sprawdzonych usług, takich jak `Proton VPN` czy `Mullvad`.

## Podsumowanie

Prywatność to proces, a nie stan zero-jedynkowy. Nie musisz wyrzucać telefonu ani rezygnować z technologii. Wdrożenie tych kilku kroków sprawi, że Ty i Twój telefon przestaniecie być otwartą księgą dla komercyjnych firm. Wystarczy zacząć od małych, świadomych zmian.
