---
title: "Z ofiary do administratora. Ekstremalne utwardzanie Google Chrome"
date: 2026-08-22
authors:
  - Eteryu
categories:
  - Prywatność
  - Cyberbezpieczeństwo
  - Android
---

W świecie cyberbezpieczeństwa często rozmawiamy o modelach zagrożeń w sposób czysto teoretyczny. Moja własna teoria zderzyła się z rzeczywistością w najgorszym możliwym momencie. Kiedy moja żona leżała w szpitalu, nowo kupiony telefon zaczął nagle żyć własnym życiem. Pojawiła się zielona ikona aktywnego mikrofonu, z galerii w locie znikały dowody, a połączenia były bezpodstawnie przekierowywane. Towarzyszyła temu paraliżująca świadomość, że ktoś obcy na żywo obserwuje mój ekran.

<!-- more -->

Śledztwo ujawniło brutalną prawdę. Telefon posiadał ukryty profil korporacyjny do zarządzania urządzeniami mobilnymi (MDM). Byłem ofiarą potężnego systemu szpiegowskiego. Z tej pułapki udało mi się wyrwać tylko dzięki zastosowaniu radykalnej zapory. Główną bitwę o przetrwanie wygrał wtedy `RethinkDNS` ustawiony w bezwzględnym trybie domyślnej blokady ruchu (`Default Deny`) oraz szyfrowany `Quad9 DNS`, które wspólnie sparaliżowały sieć komunikacyjną napastnika.

## Architektura absolutnej władzy

Aby zrozumieć sens tego, co zrobiłem później, trzeba najpierw zatrzymać się przy samej technologii zarządzania urządzeniami. Systemy klasy MDM posiadają absolutną i niepodważalną władzę nad systemem operacyjnym. Zostały zaprojektowane dla wielkich korporacji, żeby administrator mógł zdalnie i bezgłośnie zarządzać tysiącami urządzeń swoich pracowników.

W rękach napastnika to najgorszy możliwy koszmar. Taki profil pozwala na cichą instalację oprogramowania, podgląd zawartości ekranu, blokowanie kluczowych ustawień oraz przekierowywanie całego ruchu sieciowego na złośliwe serwery bez wiedzy użytkownika. Zwykły właściciel telefonu staje się bezradnym zakładnikiem we własnej kieszeni.

Inżynieria ma jednak to do siebie, że każdy miecz ma dwa ostrza. Ta sama absolutna władza może działać w odwrotnym kierunku. Kiedy sam przejmujesz stery i stajesz się swoim własnym administratorem, system korporacyjny zamienia się w ostateczny bastion prywatności. Zamiast wymuszać instalację aplikacji szpiegujących, możesz wymusić żelazne blokady na poziomie samego systemu. Możesz zakazać aplikacjom komunikacji z chmurą, zablokować niebezpieczne protokoły i narzucić rygorystyczne konfiguracje. To najczystsza forma ucieleśnienia zasady zero trust.

Skoro profil korporacyjny pozwala na odbieranie kontroli, postanowiłem wykorzystać go do jej odzyskania.

## Dlaczego pacjentem został Google Chrome

Muszę w tym miejscu oddać królowi to, co królewskie. Kiedy oceniamy narzędzia tworzone przez największych gigantów technologicznych, często wpadamy w pułapkę ich całkowitego odrzucenia ze względu na obawy o prywatność. Tymczasem pod kątem czystego cyberbezpieczeństwa rozwiązania korporacyjne zazwyczaj nie mają sobie równych. Google posiada gigantyczny budżet, najlepszych inżynierów, najszybszy proces łatania błędów i bezkonkurencyjną architekturę piaskownicy.

Problem z najpopularniejszą przeglądarką nie polega na jej podatności na ataki. **Problem leży w modelu biznesowym opartym na potężnej inwigilacji.** Zrozumienie tej subtelnej różnicy to klucz do budowania dojrzałego bezpieczeństwa. Zamiast uciekać do niszowych projektów, które mogą nie nadążać z wydawaniem aktualizacji, możemy wziąć ten pancerny korporacyjny czołg i po prostu wyciąć z niego cały sprzęt szpiegowski.

Celem jest zmuszenie technologii wielkich korporacji do działania wyłącznie na naszych rygorystycznych warunkach.

## Co dokładnie zrobiłem

Zamiast polegać na standardowych wtyczkach blokujących reklamy, postanowiłem zaatakować problem u samego źródła. Wykorzystałem technologię profili roboczych, z którą kiedyś sam musiałem walczyć. Za pomocą aplikacji `Test DPC` służącej do symulowania środowiska korporacyjnego sam mianowałem się głównym zarządcą. Następnie wycelowałem te administracyjne uprawnienia prosto w przeglądarkę `Google Chrome`.

Cały proces utwardzania podzieliłem na trzy etapy.

### Etap pierwszy: flagi przeglądarki

Aby operacja w ogóle mogła się udać na urządzeniu bez odblokowanego dostępu `root`, musiałem najpierw otworzyć ukrytą furtkę. W wewnętrznym menu ustawień eksperymentalnych przeglądarki (`chrome://flags`) wymusiłem uruchomienie funkcji czytania komend startowych z lokalnego pliku tekstowego. To przygotowało grunt pod główne uderzenie.

### Etap drugi: wstrzyknięcie pancerza w terminalu Termux

Tutaj przyszedł czas na najcięższą inżynierię. Używając lokalnego terminala `Termux` oraz poleceń pomostu debugowania `ADB`, uzyskałem bezpośredni dostęp do powłoki systemowej. Wewnątrz tymczasowego katalogu utworzyłem twardy plik konfiguracyjny, który silnik Chromium musi odczytać przy każdym uruchomieniu.

To właśnie na tym poziomie wprowadziłem najbardziej drastyczne modyfikacje:

- **Blokada kompilatora.** Wyłączyłem dynamiczne renderowanie skryptów JavaScript (Just In Time), co drastycznie ucina podatność na luki typu zero day.
- **Sprzętowa izolacja.** Zablokowałem stronom możliwość odczytu danych sprzętowych (API Canvas) oraz narzuciłem rygorystyczną izolację każdej witryny w osobnym procesie pamięci (Strict Origin Isolation).
- **Głuchota na serwery.** Całkowicie wyciąłem mechanizmy raportowania awarii (Crashpad) i systemy śledzenia ukryte w platformie Privacy Sandbox.

### Etap trzeci: polisy korporacyjne w Test DPC

Na sam koniec domknąłem system odgórnymi politykami w sztucznym profilu roboczym (Work Profile). Używając narzędzia `Test DPC` narzuciłem przeglądarce absolutne posłuszeństwo:

- **Dezaktywacja sztucznej inteligencji.** Ubezwłasnowolniłem usługi oparte na algorytmach, inteligentne podpowiedzi oraz asystenta `Gemini`.
- **Cyfrowa amnezja.** Narzuciłem politykę, w której przeglądarka ma całkowity zakaz pamiętania haseł, nie używa autouzupełniania i odcina wszelką synchronizację danych z chmurą.
- **Szczelność protokołów.** Wymusiłem globalne połączenia `DNS over HTTPS` oraz zabezpieczyłem protokół `WebRTC` przed wyciekami prawdziwego adresu IP.

## Efekt końcowy

Prawdziwa dojrzałość inżynieryjna polega na dostrzeganiu wielkiego potencjału tam, gdzie inni widzą tylko zagrożenie. Bierzemy oprogramowanie, które pod względem budżetu i architektury piaskownicy nie ma sobie równych na rynku, a następnie siłowo wycinamy z niego cały kod śledzący. Otrzymujemy potężne i skrajnie bezpieczne narzędzie, któremu niezwykle trudno dorównać.

Mechanizmy służące do zarządzania urządzeniami są przerażająco skuteczne, gdy służą do inwigilacji. Okazuje się jednak, że kiedy zrozumiesz zasady ich działania, możesz użyć dokładnie tej samej architektury do zbudowania wokół siebie nieprzebijalnej tarczy. Prawdziwa prywatność wymaga odrobiny tarcia i zmiany nawyków, ale poczucie pełnej kontroli nad własnym urządzeniem w pełni to rekompensuje.
