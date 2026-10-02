---
title: "Cyfrowa higiena podczas przerwy na kawę. Jak łatwo odzyskać kontrolę nad telefonem?"
date: 2026-06-24
authors:
  - Eteryu
categories:
  - Prywatność
  - Android
---

Ostatnia afera w Poznaniu wokół śledzenia użytkowników i brokerów danych znowu przypomniała nam o jednym: nasze smartfony bez przerwy nadają o tym, gdzie jesteśmy i co robimy. Dobra wiadomość jest taka, że odcięcie większości tego komercyjnego szpiegowania wcale nie wymaga bycia ekspertem od cyberbezpieczeństwa.

To kwestia kilku prostych nawyków, które wdrożysz na swoim telefonie właśnie podczas krótkiej przerwy na kawę.

<!-- more -->

## 1. Zmyj swój cyfrowy tatuaż

Większość z nas nosi w kieszeni unikalny numer ukryty głęboko w systemie, tak zwany **identyfikator reklamowy**. To właśnie ten cyfrowy tatuaż pozwala firmom marketingowym i brokerom danych łączyć Twoje luźne ruchy w różnych aplikacjach w jeden spójny profil.

=== "Android"

    Począwszy od systemu Android 12, Google umożliwiło użytkownikom całkowite usunięcie identyfikatora reklamowego. W celu jego trwałego usunięcia należy wykonać poniższe kroki:

    1. Otwórz główne **Ustawienia** telefonu i przejdź do zakładki **Google** (lub `Usługi Google`).
    2. Wybierz kartę `Wszystkie usługi`, a następnie kliknij w sekcję **Reklamy**.
    3. Wybierz opcję **„Usuń identyfikator reklamowy”** i potwierdź swój wybór.

    !!! info "Starsze wersje systemu (Android 11 i niżej)"

        Na starszych urządzeniach opcja całkowitego usunięcia może nie być dostępna. Wtedy w tym samym menu warto wybrać opcję nakazującą systemowi zablokowanie personalizacji reklam.

    Jeśli ekran jest zupełnie pusty i widzisz tylko pojedynczy link informacyjny, to gratulacje. Oznacza to, że po wcześniejszym wyłączeniu personalizacji reklam bezpośrednio na swoim koncie Google, system automatycznie wykasował ten identyfikator z poziomu urządzenia.

    ![Tak wygląda poprawnie wyczyszczony ekran reklamowy Google w systemie Android](https://i.postimg.cc/zG2m1BbS/Resized-Image-2026-06-24-13-43-21-9511.png)

=== "iOS (Apple)"

    Apple rozwiązuje ten problem systemowo. Funkcja `App Tracking Transparency` sprawia, że przy instalacji aplikacji wystarczy kliknąć „Poproś aplikację o nieśledzenie”.

    W ustawieniach systemowych warto też wyłączyć opcję **„Pozwalaj aplikacjom żądać możliwości śledzenia”**, co odcina aplikacjom samą możliwość wyświetlania takich zapytań. Apple posiada również własny system reklamy ukierunkowanej, który można wyłączyć w sekcji **Reklamy Apple** w ustawieniach prywatności.

W obu przypadkach cel zostaje osiągnięty: dla całego przemysłu reklamowego stajesz się czystą kartą.

## 2. Wielka czwórka uprawnień: Lokalizacja, Sieć, Tło i ukryte skanowanie

Zanim bezrefleksyjnie klikniesz „Zezwól” przy kolejnym wyskakującym okienku po instalacji nowej aplikacji, zatrzymaj się na sekundę. Aby aplikacja mogła Cię skutecznie profilować, musi zebrać dane, działać po cichu, kiedy śpisz, i mieć jak wysłać te paczki na serwer brokerów.

Oto jak skutecznie rozbić ten proces na czynniki pierwsze:

- **Lokalizacja to nie przymus (Case pogodynki i taksówek).** Aplikacje do zamawiania taksówek oraz pogodynki świetnie dadzą sobie radę bez GPS, wystarczy ręcznie wpisać adres lub nazwę miasta. Zamiast usług od Google czy Apple, możesz postawić na rozwiązania w stu procentach lokalne i otwartoźródłowe, takie jak `Organic Maps` czy `OsmAnd`. Wgrywasz do nich pobrane wcześniej mapy i podróżujesz całkowicie offline. Jeśli natomiast jakaś inna apka koniecznie domaga się lokalizacji, zawsze wybieraj opcję **„przybliżona”** zamiast precyzyjnej.
- **Ukryte radary (Skanowanie Wi-Fi i Bluetooth).** Większość ludzi myśli, że jak wyłączy GPS, to jest niewidzialna. Nic bardziej mylnego. Telefony domyślnie przeczesują otoczenie w poszukiwaniu routerów i beaconów reklamowych, nawet gdy masz te moduły oficjalnie wyłączone. Brokerzy danych używają tych sygnałów, by wiedzieć, przy której półce sklepowej stoisz. Wejdź w ustawienia lokalizacji, znajdź sekcję `Skanowanie Wi-Fi i Bluetooth` i wyłącz obie te opcje.
- **Odcięcie od sieci, po co im internet?** Jeśli aplikacja (np. czytnik PDF, kalkulator czy gra jednoosobowa) działa w stu procentach lokalnie, warto zablokować jej dostęp do internetu komórkowego i Wi-Fi. Choćby zebrała tonę statystyk wewnątrz telefonu, bez dostępu do sieci nie ma jak wysłać ich w świat.

    !!! tip "Blokada sieci na czystym Androidzie"

        Nakładki takie jak `One UI` (Samsung) czy `HyperOS` (Xiaomi) mają wbudowane opcje blokowania sieci w ustawieniach aplikacji. Jeśli używasz „czystego” Androida, np. na Pixelu, możesz użyć prostej i bezpiecznej aplikacji typu firewall, na przykład `NetGuard`.

- **Koniec z pracą na trzy zmiany (Działanie w tle).** Wiele aplikacji żyje własnym życiem, kiedy z nich nie korzystasz. Wejdź w ustawienia aplikacji (lub baterii) i dla wszystkiego, co nie musi wysyłać Ci natychmiastowych powiadomień, całkowicie wyłącz opcję **„Zezwalaj na działanie w tle”** (`Allow background usage`). Telefon nie tylko przestanie nadawać za Twoimi plecami, ale też podziękuje Ci za to znacznie dłuższym czasem pracy na jednym ładowaniu.

## 3. Postaw systemową tarczę na trackery

Wszystko, co mimo powyższych blokad spróbuje wysłać zapytanie z Twojego telefonu, można przefiltrować w locie, zanim w ogóle dotrze do serwerów szpiegujących czy analitycznych. Masz do wyboru dwie najprostsze drogi:

- **Prywatny DNS (Darmowy i lekki).** To genialna funkcja wbudowana w każdy nowoczesny telefon. Wchodzisz w ustawienia sieciowe, znajdujesz opcję `Prywatny DNS` i wpisujesz tam darmowy adres filtrujący, na przykład od `NextDNS` lub `AdGuard`. Od tej sekundy system sam automatycznie blokuje zapytania do znanych sieci reklamowych.
- **VPN z filtrem (Wygoda Premium).** Jeśli zależy Ci nie tylko na blokowaniu trackerów, ale chcesz też zamaskować swój adres IP i zaszyfrować ruch, świetnym rozwiązaniem są sprawdzone usługi takie jak **Proton VPN** czy **Mullvad**.

## Podsumowanie: Prywatność to proces

Prywatność to proces, a nie stan zero czy jeden. Nie musisz nagle wyrzucać telefonu ani rezygnować z technologii. Wdrożenie tych kilku prostych kroków sprawi, że Ty i Twój telefon przestaniecie być otwartą księgą dla komercyjnych firm. Cyfrowa higiena jest prosta, wystarczy zacząć od małych, świadomych zmian.
