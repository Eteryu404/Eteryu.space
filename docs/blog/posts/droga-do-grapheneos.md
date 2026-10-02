---
date: 2026-06-05
categories:
  - Prywatność
  - Cyberbezpieczeństwo
  - GrapheneOS
---

# Jak okiełznałem system z MDM. Moja droga do GrapheneOS

W świecie cyberbezpieczeństwa często rozmawiamy o „modelach zagrożeń” (Threat Models) w sposób czysto teoretyczny. Analizujemy tabelki, czytamy dokumentację i zastanawiamy się, czy korporacyjny szum telemetryczny to wystarczający powód do zmiany nawyków. Sam byłem w tym miejscu, budując swój poprzedni setup na iPhonie 17 Pro. Wszystko zmieniło się w ułamku sekundy, gdy teoria zderzyła się z brutalną rzeczywistością.

<!-- more -->

Gdy moja żona nagle trafiła do szpitala, priorytety zmieniły się w mgnieniu oka. Aby podreperować budżet, sprzedałem iPhone'a, a za ułamek zdobytej kwoty kupiłem z drugiej ręki Pixela 8. Od dawna interesowałem się rozwiązaniami *privacy-focused* oraz ruchem FOSS, więc ten model był naturalnym kierunkiem — docelowo miał na nim wylądować GrapheneOS. Na tamten moment nie posiadaliśmy jednak w domu komputera, ale jak się później okazało... to i tak nic by nie zmieniło. Ukryty profil MDM, który znajdował się na telefonie, skutecznie zablokowałby każdą próbę odblokowania bootloadera i flashowania systemu. Musiałem więc uruchomić go na oprogramowaniu fabrycznym.

Chcę Wam opowiedzieć o incydencie, który zmusił mnie do natychmiastowej ewakuacji cyfrowej tożsamości i o tym, jak techniki obronne pozwoliły mi przetrwać najgorszy moment.

## Kiedy Twój telefon zaczyna żyć własnym życiem

To był potwornie ciężki okres. Moja żona leżała w szpitalu, a telefon był moim jedynym, krytycznym oknem na świat i jedynym źródłem informacji o jej stanie zdrowia. Połowa moich myśli była na oddziale szpitalnym, gdy nagle zauważyłem, że mój nowo kupiony Pixel 8 zachowuje się nietypowo.

Zaczęło się od drobnych anomalii, które szybko przerodziły się w techniczny koszmar:

* **Aktywny podsłuch:** Na ekranie pojawiała się zielona ikona aktywnego mikrofonu, mimo że nie prowadziłem żadnej rozmowy ani nie używałem aplikacji dyktafonu.
* **Zdalne sterowanie:** Telefon losowo wykonywał akcje, jakby ktoś sterował nim w czasie rzeczywistym.
* **Manipulacja danymi:** Z systemowej galerii Google Photos zaczęły znikać pojedyncze zdjęcia i zrzuty ekranu.
* **Intercepcja połączeń:** Zauważyłem bezpodstawne przekierowania moich połączeń przychodzących na obcy, nieznany numer.

Najgorszy był efekt "migawki" — ekran zachowywał się tak, jakby ktoś robił zrzuty ekranu w locie. W warunkach skrajnego stresu rodzinnego, świadomość, że ktoś obcy patrzy na mój ekran i słucha mojego otoczenia, była paraliżująca.

## Śledztwo w trybie naprawy: Syndrom MDM

Wiedziałem, że standardowy restart nic nie da. Wyłączyłem urządzenie i uruchomiłem je w trybie naprawy (*Recovery/Repair Mode*). To tam klocki układanki wreszcie wpadły na swoje miejsce.

[!attention]
**Komunikat systemowy:** *„Urządzenie jest kontrolowane przez administratora...”*
![Systemowy komunikat o blokadzie i profilu MDM na systemie Android](https://i.postimg.cc/KvrXfSFp/p2i6euqh9irf1.png)

Telefon posiadał ukryty, nadrzędny profil **MDM (Mobile Device Management)**. Ktoś sprzedał mi urządzenie korporacyjne jako czysty sprzęt konsumencki. Profil MDM dawał zdalnemu napastnikowi uprawnienia administracyjne wyższe niż moje własne. Mógł w locie podglądać ekran, aktywować sensory i manipulować routingiem połączeń.

Sprawę natychmiast zgłosiłem na Policję, a urządzenie zostało zakwalifikowane do zwrotu. Pojawił się jednak kluczowy problem: jak bezpiecznie przeczekać kilka dni, mając na telefonie krytyczne konta bankowe, mailowe i komunikatory, w dodatku bez możliwości odcięcia się od sieci ze względu na sytuację w szpitalu?

## Incident Response w warunkach bojowych

Musiałem działać jak inżynier w strefie konfliktu. Zastosowałem podręcznikową taktykę izolacji skażonego hosta za pomocą trzech kroków:

[!info] **Krok 1: Bezpieczny bastion dla dowodów (ente Photos)**
Zanim zacząłem głębszą konfigurację, zabezpieczyłem zrzuty ekranu dokumentujące aktywność aplikacji oraz sam komunikat o MDM. Ponieważ napastnik usuwał pliki z Google Photos, zainstalowałem **ente Photos** — w pełni szyfrowaną (E2EE) alternatywę. Dzięki temu napastnik stracił możliwość manipulowania dowodami dla Policji.

[!info] **Krok 2: Zapora ogniowa w trybie Default-Deny**
Zainstalowałem lokalny firewall **RethinkDNS** i przełączyłem go w tryb całkowitej blokady ruchu wychodzącego. Ręcznie tworzyłem białą listę zaufanych aplikacji. Odcięcie procesów `Shell` oraz `SystemUI` od sieci sparaliżowało architekturę Command & Control (C2) napastnika.

[!info] **Krok 3: Szyfrowany i filtrowany DNS od Quad9**
W RethinkDNS zmieniłem routing zapytań na **Quad9 DNS**, który automatycznie dropuje zapytania do znanych złośliwych domen i serwerów botnetowych.

Dzięki tej sterylnej kwarantannie zyskałem cenny czas. Wszystkie dowody przesłałem prowadzącej sprawę policjantce za pomocą bezpiecznej skrzynki **Tuta Mail**. W tym środowisku spokojnie zmieniłem hasła i klucze sesyjne we wszystkich krytycznych usługach.

## Nowy początek: GrapheneOS jako cyfrowa forteca

Po odesłaniu wadliwego urządzenia skontaktowałem się ze sprzedawcą. W ramach wymiany otrzymałem pewny egzemplarz Pixela 8, a serwisant **samodzielnie wgrał GrapheneOS na nowy telefon przed wysyłką**, aby mieć pewność, że sprzęt jest 100% czysty.

Wgranie GrapheneOS całkowicie eliminuje ryzyko przetrwania ukrytych profilów korporacyjnych (dzięki mechanizmowi Verified Boot). Na tym systemie buduję swój obecny Threat Model, oparty na braku ślepego zaufania (Zero Trust):

* **Całkowita de-googlizacja:** Profil główny jest wolny od kodu Google (FOSS). Używam menedżerów **Obtainium** i **Accrescent**.
* **Ścisła izolacja (Multiple Profiles):** Usługi komercyjne i Google Play zamknąłem w odizolowanym profilu użytkownika z ograniczonym dostępem do sieci.
* **Separacja sieciowa:** Ruch obu profili jest odseparowany przez niezależne instancje WireGuard w trybie Always-on.

## Wnioski na przyszłość

Prywatność i cyberbezpieczeństwo to nie są hobbystyczne fanaberie. Skompromitowane urządzenie mobilne to bezpośrednie zagrożenie dla Twojego życia osobistego, finansów i spokoju psychicznego.

[!tip]
Jeśli podejrzewasz, że Twój system zachowuje się nienaturalnie — nie czekaj. Odetnij procesy systemowe od sieci, zabezpiecz tożsamość za pomocą szyfrowanych narzędzi i szukaj rozwiązań, które dają Ci pełną kontrolę nad sprzętem. Dla mnie tą jedyną odpowiedzią stał się duet czystego sprzętu i GrapheneOS.
