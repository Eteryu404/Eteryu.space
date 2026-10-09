---
title: Katalog Oprogramowania
description: Rygorystycznie wyselekcjonowany katalog narzędzi open source zorientowanych na prywatność. Aplikacje, przeglądarki, DNS, VPN i menedżery haseł.
icon: lucide/list
---

# Katalog oprogramowania 

!!! abstract "Kryteria wyboru"
    Katalog zawiera rygorystycznie wyselekcjonowane narzędzia cyfrowe zorientowane na prywatność. Zestawienie obejmuje wyłącznie rozwiązania zweryfikowane w praktyce oraz aplikacje otwartoźródłowe, rozwiązania z dostępnym kodem do wglądu i w pełni lokalne środowiska zamknięte.

    Narzędzia te stanowią fundament budowy architektury Zero Trust oraz skutecznej minimalizacji cyfrowego śladu. Ograniczenia i czerwone flagi są opisane wprost przy każdym narzędziu.

## Zarządzanie aplikacjami

<div class="grid cards" markdown>

-   :material-package-variant: **Obtainium**
    
    ---
    
    Uniwersalne narzędzie pobierające i automatycznie aktualizujące aplikacje bezpośrednio z ich oficjalnych stron wydań. Pozwala całkowicie ominąć sklepy pośredniczące i zachować kontrolę nad źródłem instalacji.
    
    [➔ Przejdź do repozytorium](https://github.com/ImranR98/Obtainium)

-   :material-shield-check: **App Verifier BG**
    
    ---
    
    Utwardzony, działający w tle fork narzędzia AppVerifier. Stale weryfikuje spójność oraz autentyczność podpisów zainstalowanych aplikacji, ostrzegając przed nieautoryzowaną modyfikacją.
    
    [➔ Przejdź do repozytorium](https://github.com/RoundSalmon4/AppVerifierBG)

-   :material-check-decagram: **Verified Apps**
    
    ---
    
    Narzędzie wspierające weryfikację autentyczności aplikacji Android poprzez porównywanie podpisów i skrótów z zaufanymi źródłami. Ogranicza ryzyko instalacji zmodyfikowanych paczek.
    
    [➔ Przejdź do repozytorium](https://github.com/privacyguides/verified-apps-android)

-   :material-store-search: **Komi Store**
    
    ---
    
    Otwarty sklep agregujący aplikacje publikowane bezpośrednio na platformach dla deweloperów. Ułatwia wygodne odkrywanie i instalowanie projektów bez konieczności ręcznego szukania plików instalacyjnych.
    
    [➔ Przejdź do repozytorium](https://github.com/kurikomi-labs/komi-store)

-   :material-lock: **Accrescent**
    
    ---
    
    Utwardzony, nowoczesny sklep z aplikacjami posiadający zweryfikowaną bibliotekę programów. Wymusza rygorystyczne sprawdzanie podpisów cyfrowych i szyfrowane metadane.
    
    [➔ Przejdź do repozytorium](https://github.com/accrescent/accrescent)

</div>

## Przeglądarki internetowe

<div class="grid cards" markdown>

-   :material-shield-search: **Vanadium**
    
    ---
    
    Utwardzona przeglądarka systemu GrapheneOS skupiona na izolacji piaskownicy i rygorystycznej ochronie pamięci. Zapewnia najniższą powierzchnię ataku sieciowego.
    
    [➔ Przejdź do repozytorium](https://github.com/GrapheneOS/Vanadium)

-   :fontawesome-brands-brave: **Brave**
    
    ---
    
    Uniwersalna i szybka przeglądarka z domyślnie wbudowaną ochroną przed trackerami. Oferuje świetny balans między wygodą a prywatnością bez konieczności ręcznej konfiguracji.
    
    [➔ Przejdź do repozytorium](https://github.com/brave/brave-browser)

-   :material-google-chrome: **Google Chrome**
    
    ---
    
    Przeglądarka o zaawansowanej architekturze bezpieczeństwa, oferująca najwyższy poziom izolacji procesów (sandbox) oraz błyskawiczne łatki Zero Day.
    
    !!! danger "Krytyczny wymóg"
        Przeglądarka wymaga rygorystycznej konfiguracji (Hardening) w celu zablokowania wbudowanej telemetrii.
    
    [➔ Przejdź do repozytorium](https://github.com/chromium/chromium)
    
</div>

## Sieć i bezpieczeństwo

<div class="grid cards" markdown>

-   :material-dns: **Quad9**
    
    ---
    
    Uniwersalna, niezależna usługa DNS nastawiona na bezpieczny routing. Automatycznie blokuje złośliwe domeny bez logowania adresu protokołu internetowego użytkownika.
    
    [➔ Przejdź do strony](https://quad9.net/)

-   :material-security: **AdGuard DNS**
    
    ---
    
    Uniwersalny, sprawdzony resolver wycinający telemetrię i reklamy na poziomie sieci. Zapewnia gotowy punkt bez konieczności logowania danych.
    
    [➔ Przejdź do strony](https://adguard-dns.io/)

-   :material-server-network: **NextDNS**
    
    ---
    
    Uniwersalna, zaawansowana usługa DNS pozwalająca na tworzenie własnych reguł filtrowania reklam. Zapewnia opcję wyłączenia logów oraz prostą konfigurację w systemie operacyjnym.
    
    [➔ Przejdź do strony](https://nextdns.io/)

-   :material-security-network: **Control D**
    
    ---
    
    Utwardzony, wysoce konfigurowalny DNS oferujący bezkompromisowe blokowanie telemetrii urządzeń z opcją precyzyjnego routowania ruchu.
    
    [➔ Przejdź do strony](https://controld.com/)

-   :material-wall: **RethinkDNS**
    
    ---
    
    Utwardzone narzędzie łączące lokalną zaporę sieciową z elastycznym filtrowaniem DNS. Umożliwia precyzyjne blokowanie połączeń dla każdej aplikacji z osobna.
    
    [➔ Przejdź do repozytorium](https://github.com/celzero/rethink-app)

-   :material-vpn: **WireGuard**
    
    ---
    
    Uniwersalny, nowoczesny i niezwykle szybki protokół oraz klient VPN. Wykorzystuje zaawansowaną kryptografię przy zminimalizowanym zużyciu baterii.
    
    [➔ Przejdź do strony](https://www.wireguard.com/install/)

-   :material-vpn: **WG Tunnel**
    
    ---
    
    Zaawansowany klient WireGuard dla Androida z automatycznym tunelowaniem, wieloma profilami i regułami split tunneling. Rozszerza standardowego klienta o wygodę i kontrolę.
    
    [➔ Przejdź do repozytorium](https://github.com/wgtunnel/android)

-   :material-shield-lock: **Mullvad VPN**
    
    ---
    
    Utwardzony dostawca VPN niewymagający podawania adresu email ani danych osobowych przy rejestracji. Oferuje wbudowane filtrowanie DNS.
    
    [➔ Przejdź do strony](https://mullvad.net/)

-   :material-shield-account: **IVPN**
    
    ---
    
    Utwardzony, audytowany dostawca VPN z jasną polityką braku logów. Umożliwia rejestrację bez danych osobowych, obsługuje WireGuard i Multi-Hop.
    
    [➔ Przejdź do repozytorium](https://github.com/ivpn/android-app)

-   :material-shield-star: **Proton VPN**
    
    ---
    
    Uniwersalny, audytowany VPN oferujący nielimitowany plan darmowy oraz autorski mechanizm ochrony przed trackerami w sieci.
    
    [➔ Przejdź do strony](https://protonvpn.com/)

</div>

## Menedżery haseł i autoryzacja

<div class="grid cards" markdown>

-   :material-form-textbox-password: **KeePassDX**
    
    ---
    
    Utwardzony, w pełni lokalny menedżer haseł. Zapewnia absolutną suwerenność danych bez polegania na zewnętrznych serwerach czy chmurze.
    
    [➔ Przejdź do repozytorium](https://github.com/Kunzisoft/KeePassDX)

-   :material-cloud-key: **Bitwarden**
    
    ---
    
    Uniwersalny i chmurowy menedżer haseł oferujący bezpieczną synchronizację. Umożliwia postawienie własnej instancji serwerowej.
    
    !!! warning "Higiena metadanych i wybór paczki"
        Standardowa kompilacja (w tym ta z Google Play) zawiera biblioteki telemetrii (np. Firebase). Przy instalacji z GitHuba (np. przez Obtainium) należy upewnić się, że pobierana jest wersja pliku APK w wariancie FOSS, która jest całkowicie wyczyszczona z modułów śledzących.
    
    [➔ Przejdź do repozytorium](https://github.com/bitwarden/android)

-   :material-key-variant: **Proton Pass**
    
    ---
    
    Uniwersalny menedżer haseł z szyfrowaniem end to end, obsługą passkeys, aliasów email oraz integracją z ekosystemem Proton. Kod aplikacji Android jest dostępny publicznie.
    
    [➔ Przejdź do repozytorium](https://github.com/protonpass/android-pass)

-   :material-two-factor-authentication: **Aegis**
    
    ---
    
    Utwardzona, szyfrowana aplikacja do generowania kodów dwuskładnikowych działająca całkowicie w trybie offline z opcją tworzenia kopii zapasowych.
    
    [➔ Przejdź do repozytorium](https://github.com/beemdevelopment/Aegis)

-   :material-key-chain: **2FAS**
    
    ---
    
    Uniwersalny i intuicyjny authenticator z opcją w pełni szyfrowanej kopii zapasowej we własnej chmurze.
    
    [➔ Przejdź do repozytorium](https://github.com/twofas/2fas-android)

-   :material-shield-key: **Ente Auth**
    
    ---
    
    Uniwersalny, wieloplatformowy authenticator wykorzystujący szyfrowanie end to end z możliwością synchronizacji między wieloma urządzeniami.
    
    [➔ Przejdź do repozytorium](https://github.com/ente/ente)

</div>

## Komunikacja i poczta

<div class="grid cards" markdown>

-   :material-message-lock: **Molly**
    
    ---
    
    Utwardzona wersja komunikatora Signal z dodatkowym szyfrowaniem bazy danych w spoczynku i ochroną pamięci.
    
    [➔ Przejdź do repozytorium](https://github.com/mollyim/mollyim-android)

-   :material-email-check: **Tuta Mail**
    
    ---
    
    Uniwersalny klient bezpiecznej i kompleksowo szyfrowanej poczty email chroniący dane w modelu Zero Knowledge.
    
    [➔ Przejdź do repozytorium](https://github.com/tutao/tutanota)

-   :material-email-lock: **Proton Mail**
    
    ---
    
    Uniwersalny klient poczty oferujący szyfrowanie end to end, samoniszczące wiadomości i ochronę przed trackerami w mailach. Kod aplikacji jest dostępny na GitHubie na licencji GPLv3.
    
    !!! warning "Higiena metadanych i wybór paczki"
        Aplikacja zawiera biblioteki Google (Firebase) oraz Sentry do raportowania błędów. Dotyczy to zarówno wersji z Google Play, jak i gotowych plików APK publikowanych w GitHub Releases. Sentry jest wyłączone wyłącznie w buildach kompilowanych samodzielnie ze źródeł, bez ustawiania zmiennych `SENTRY_DSN_MAIL` i `SENTRY_DSN_ACCOUNT`. Jeśli nie kompilujesz aplikacji samodzielnie, musisz zaakceptować obecność tych bibliotek.
    
    [➔ Przejdź do repozytorium](https://github.com/ProtonMail/android-mail)

-   :material-email-plus: **Addy.io**
    
    ---
    
    Uniwersalna usługa do tworzenia anonimowych aliasów pocztowych, skutecznie chroniąca przed profilowaniem behawioralnym.
    
    [➔ Przejdź do repozytorium](https://github.com/anonaddy/addy-android)

-   :material-email-lock: **SimpleLogin**
    
    ---
    
    Uniwersalny i otwarty menedżer aliasów pozwalający na izolację głównej skrzynki odbiorczej przed niechcianym śledzeniem.
    
    [➔ Przejdź do repozytorium](https://github.com/simple-login/Simple-Login-Android)

</div>

## Notatki i organizacja

<div class="grid cards" markdown>

-   :material-notebook: **Obsidian**
    
    ---
    
    Potężny edytor oparty na plikach lokalnych. Używany w modelu Zero Trust z całkowicie zablokowanym dostępem do sieci i wyizolowaną pamięcią.
    
    !!! warning "Zamknięty kod źródłowy"
        Obsidian to oprogramowanie komercyjne (Proprietary). Pomimo faktu, że pliki przechowywane są w 100% lokalnie, sam kod nie podlega publicznym audytom bezpieczeństwa FOSS, a darmowa licencja wyklucza użycie firmowe.
    
    [➔ Przejdź do strony](https://obsidian.md/)

-   :material-notebook-edit: **Notesnook**
    
    ---
    
    Otwartoźródłowy, szyfrowany end to end menedżer notatek z synchronizacją, trybem offline i ochroną przed analityką. Pozwala zachować kontrolę nad danymi.
    
    [➔ Przejdź do repozytorium](https://github.com/streetwriters/notesnook)

-   :material-note-edit: **Quillpad**
    
    ---
    
    Uniwersalny notatnik z przyjaznym interfejsem. Zapisuje dane w zapiaskowanej bazie lokalnej, łącząc estetykę z bezpieczeństwem.
    
    [➔ Przejdź do repozytorium](https://github.com/quillpad/quillpad)

-   :material-note-text: **Markor**
    
    ---
    
    Uniwersalny edytor czystego tekstu działający w pełni offline. Nie posiada uprawnień sieciowych i zapisuje pliki bezpośrednio w pamięci urządzenia.
    
    [➔ Przejdź do repozytorium](https://github.com/gsantner/markor)

-   :material-text-box-edit: **NotallyX**
    
    ---
    
    Rozbudowany, lekki fork popularnego notatnika pozbawiony wbudowanych trackerów.
    
    [➔ Przejdź do repozytorium](https://github.com/Crustack/NotallyX)

-   :material-brain: **Logseq**
    
    ---
    
    Uniwersalna baza wiedzy o strukturze blokowej. Gwarantuje pełną suwerenność dzięki pracy wyłącznie w trybie offline bez wymuszonej synchronizacji.
    
    [➔ Przejdź do repozytorium](https://github.com/logseq/logseq)

-   :material-file-document-edit: **CryptPad**
    
    ---
    
    Szyfrowana end to end platforma do współpracy nad dokumentami, arkuszami, prezentacjami i tablicami. Model Zero Knowledge, możliwość self-hostingu.
    
    [➔ Przejdź do repozytorium](https://github.com/cryptpad/cryptpad)

</div>

## Kalendarze

<div class="grid cards" markdown>

-   :material-calendar-lock: **Tuta Calendar**
    
    ---
    
    Uniwersalny kalendarz oferujący pełne szyfrowanie end to end. Chroni harmonogram przed wglądem dostawcy zgodnie z modelem Zero Knowledge.
    
    [➔ Przejdź do repozytorium](https://github.com/tutao/tutanota)

-   :material-calendar-check: **Proton Calendar**
    
    ---
    
    Uniwersalny i prywatny kalendarz automatycznie zabezpieczający dane po stronie klienta bez profilowania.
    
    [➔ Przejdź do strony](https://protonapps.com/protoncalendar-android)

-   :material-calendar-blank: **Fossify Calendar**
    
    ---
    
    Uniwersalny i lokalny kalendarz pozbawiony trackerów oraz uprawnień sieciowych. Stanowi bezpieczne narzędzie do notatek offline.
    
    [➔ Przejdź do repozytorium](https://github.com/FossifyOrg/Calendar)

</div>

## Przechowywanie danych i chmura

<div class="grid cards" markdown>

-   :material-cloud-lock: **Filen**
    
    ---
    
    Uniwersalny klient chmury oferujący rygorystyczne szyfrowanie end to end z mocnym naciskiem na architekturę Zero Knowledge.
    
    [➔ Przejdź do repozytorium](https://github.com/FilenCloudDienste/filen-ts)

-   :material-cloud-upload: **Proton Drive**
    
    ---
    
    Uniwersalny klient chmury z szyfrowaniem end to end i architekturą Zero Knowledge. Umożliwia bezpieczne przechowywanie, udostępnianie i kopie zapasowe plików.
    
    [➔ Przejdź do repozytorium](https://github.com/ProtonDriveApps/android-drive)

-   :material-safe-square: **Cryptomator**
    
    ---
    
    Otwartoźródłowe szyfrowanie plików po stronie klienta przed synchronizacją z chmurą. Tworzy sejfy, do których dostawca chmury nie ma wglądu.
    
    [➔ Przejdź do repozytorium](https://github.com/cryptomator/android)

-   :material-cloud-check: **MEGA**
    
    ---
    
    Dojrzały klient do synchronizacji plików z dostępnym kodem do wglądu oraz silnym szyfrowaniem po stronie klienta.
    
    [➔ Przejdź do repozytorium](https://github.com/meganz/android)

</div>

## Synchronizacja i transfer

<div class="grid cards" markdown>

-   :material-wifi-arrow-left-right: **LocalSend**
    
    ---
    
    Uniwersalne narzędzie do błyskawicznego przesyłania plików między systemami w szyfrowanej sieci lokalnej bez użycia zewnętrznych serwerów.
    
    [➔ Przejdź do repozytorium](https://github.com/localsend/localsend)

-   :material-folder-sync: **BasicSync**
    
    ---
    
    Uniwersalny, minimalistyczny klient służący do utrzymywania bezpiecznej synchronizacji peer to peer w tle.
    
    [➔ Przejdź do repozytorium](https://github.com/chenxiaolong/BasicSync)

</div>

## Galerie i edycja zdjęć

<div class="grid cards" markdown>

-   :material-image-lock: **Ente Photos**
    
    ---
    
    Uniwersalna alternatywa dla rozwiązań komercyjnych oferująca bezpieczne przechowywanie multimediów z szyfrowaniem end to end.
    
    [➔ Przejdź do repozytorium](https://github.com/ente/ente)

-   :material-image-multiple: **Iris Gallery**
    
    ---
    
    Utwardzona, w pełni offline galeria zdjęć z wbudowanym edytorem, inspektorem EXIF oraz prywatnym sejfem. Manifest nie żąda uprawnienia INTERNET, a audyty Exodus Privacy nie wykryły żadnych trackerów.
    
    [➔ Przejdź do repozytorium](https://github.com/MohamadOday/iris-gallery)

-   :material-image-multiple: **ReFra**
    
    ---
    
    Nowoczesna i szybka galeria zdjęć z wydajnym wariantem funkcjonującym całkowicie bez uprawnień sieciowych.
    
    [➔ Przejdź do repozytorium](https://github.com/IacobIonut01/ReFra)

-   :material-image-edit: **Image Toolbox**
    
    ---
    
    Utwardzony, wielofunkcyjny edytor obrazów działający w pełni lokalnie. Umożliwia zaawansowaną edycję oraz bezpieczne wycinanie metadanych.
    
    [➔ Przejdź do repozytorium](https://github.com/T8RIN/ImageToolbox)

</div>

## Odtwarzacze i pobieranie multimediów

<div class="grid cards" markdown>

-   :material-play-protected-content: **NewPipe**
    
    ---
    
    Uniwersalny klient wideo odtwarzający materiały w tle bez konieczności logowania i profilowania przez algorytmy serwerowe.
    
    [➔ Przejdź do repozytorium](https://github.com/TeamNewPipe/NewPipe)

-   :material-youtube-tv: **PipePipe**
    
    ---
    
    Rozbudowany fork natywnie blokujący segmenty sponsorowane i posiadający poszerzone wsparcie dla różnorodnych platform.
    
    [➔ Przejdź do repozytorium](https://github.com/InfinityLoop1308/PipePipe)

-   :material-music-circle: **Flow**
    
    ---
    
    Odtwarzacz platform wideo i audio posiadający w pełni lokalny silnik rekomendacji przetwarzany bezpośrednio na urządzeniu.
    
    [➔ Przejdź do repozytorium](https://github.com/a-edev/Flow)

-   :material-music-box: **Auxio**
    
    ---
    
    Uniwersalny odtwarzacz muzyki funkcjonujący offline, który wymusza budowanie własnej biblioteki audio na pamięci fizycznej.
    
    [➔ Przejdź do repozytorium](https://github.com/oxygencobalt/Auxio)

-   :material-download-lock: **Seal**
    
    ---
    
    Uniwersalne narzędzie oparte na silniku yt dlp do lokalnego pobierania materiałów z automatycznym uzupełnianiem metadanych.
    
    [➔ Przejdź do repozytorium](https://github.com/JunkFood02/Seal)

-   :material-download-network: **YTDLnis**
    
    ---
    
    Zaawansowany menedżer pozwalający na pobieranie kompletnych zasobów z rygorystycznym zachowaniem higieny metadanych.
    
    [➔ Przejdź do repozytorium](https://github.com/deniscerri/ytdlnis)

</div>

## Narzędzia systemowe i pogoda

<div class="grid cards" markdown>

-   :material-keyboard-variant: **HeliBoard**
    
    ---
    
    Uniwersalna i w pełni konfigurowalna klawiatura ekranowa, która nigdy nie łączy się z siecią, gwarantując prywatność wprowadzanych danych.
    
    [➔ Przejdź do repozytorium](https://github.com/HeliBorg/HeliBoard)

-   :material-microphone-variant: **FUTO Keyboard**
    
    ---
    
    Utwardzona klawiatura wyposażona w zaawansowany moduł przetwarzania głosu działający całkowicie lokalnie i offline.
    
    !!! info "Licencja typu Source-Available"
        Aplikacja udostępnia kod do pełnego wglądu, jednak ze względu na ograniczenia licencyjne nałożone przez FUTO, nie spełnia klasycznej definicji wolnego oprogramowania (FOSS).
    
    [➔ Przejdź do repozytorium](https://github.com/futo-org/android-keyboard)

-   :material-weather-partly-cloudy: **Breezy Weather**
    
    ---
    
    Uniwersalna aplikacja pogodowa oparta na wyselekcjonowanych i bezpiecznych źródłach danych pozbawiona modułów analitycznych.
    
    [➔ Przejdź do repozytorium](https://github.com/breezy-weather/breezy-weather)

</div>

## Mapy i nawigacja

<div class="grid cards" markdown>

-   :material-map-marker-path: **CoMaps**
    
    ---
    
    Otwartoźródłowa nawigacja offline oparta na OpenStreetMap. Działa bez trackerów i nie wymaga konta, zapewniając prywatne planowanie tras oraz mapy do pobrania.
    
    [➔ Przejdź do repozytorium](https://github.com/comaps/comaps)

</div>
