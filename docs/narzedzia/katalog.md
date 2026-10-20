---
title: Katalog Oprogramowania
description: Ekspercki wybór narzędzi open source dla architektury Zero Trust. Aplikacje, przeglądarki, DNS i menedżery haseł zweryfikowane w praktyce.
icon: lucide/list
---

# Katalog oprogramowania 

!!! abstract "Filozofia katalogu"
    To nie jest lista aplikacji idealnych, bo takie nie istnieją. To **kuratorski wybór narzędzi** opartych na architekturze Zero Trust, których działanie i kompromisy zostały zweryfikowane w praktyce.
    
    Zgodnie z filozofią *distrust*, zamiast ukrywać wady, pokazujemy je wprost. Jeśli aplikacja zbiera metadane lub korzysta z zewnętrznych bibliotek, informacja o tym znajduje się w jej opisie. Świadome bezpieczeństwo polega na znajomości ograniczeń narzędzi i dopasowaniu ich do własnego modelu zagrożeń, a nie na ślepej pogoni za iluzją 100% prywatności.

## Zarządzanie aplikacjami i weryfikacja

<div class="grid cards" markdown>

-   :material-package-variant: **Obtainium**
    
    ---
    
    Pobiera i aktualizuje aplikacje bezpośrednio z ich oficjalnych repozytoriów (GitHub, GitLab itp.). Całkowicie omija sklepy pośredniczące, dając Ci pełną kontrolę nad źródłem kodu.
    
    [➔ Przejdź do repozytorium](https://github.com/ImranR98/Obtainium)

-   :material-lock: **Accrescent**
    
    ---
    
    Nowoczesny, utwardzony sklep z aplikacjami (dostępny m.in. na GrapheneOS) wymuszający rygorystyczne sprawdzanie podpisów cyfrowych i szyfrowane metadane.
    
    [➔ Przejdź do repozytorium](https://github.com/accrescent/accrescent)

-   :material-shield-check: **AppVerifier (BG)**
    
    ---
    
    Utwardzony fork narzędzia do weryfikacji podpisów APK. Pozwala sprawdzić, czy pobrany plik rzeczywiście pochodzi od zaufanego dewelopera, eliminując ryzyko instalacji zmodyfikowanej paczki.
    
    [➔ Przejdź do repozytorium](https://github.com/RoundSalmon4/AppVerifierBG)

-   :material-check-decagram: **Verified Apps**
    
    ---
    
    Kuratorowana przez społeczność Privacy Guides baza zaufanych sygnatur aplikacji. Uzupełnia Obtainium i AppVerifier o gotowy zestaw sprawdzonych podpisów.
    
    [➔ Przejdź do repozytorium](https://github.com/privacyguides/verified-apps-android)

</div>

## Przeglądarki internetowe

<div class="grid cards" markdown>

-   :material-shield-search: **Vanadium**
    
    ---
    
    Domyślna, utwardzona przeglądarka systemu GrapheneOS. Skupiona na izolacji piaskownicy i rygorystycznej ochronie pamięci, zapewnia najniższą powierzchnię ataku.
    
    [➔ Przejdź do repozytorium](https://github.com/GrapheneOS/Vanadium)

-   :fontawesome-brands-brave: **Brave**
    
    ---
    
    Szybka przeglądarka z domyślnie wbudowaną ochroną przed trackerami. Oferuje świetny balans między wygodą a prywatnością dla codziennego użytkowania.
    
    !!! warning "Kontrowersje"
        Brave ma historię kontrowersji, m.in. związanych z linkami afiliacyjnymi (2020) oraz innymi incydentami dotyczącymi prywatności. Mimo to pozostaje jednym z najskuteczniejszych narzędzi do blokowania trackerów.
    
    [➔ Przejdź do repozytorium](https://github.com/brave/brave-browser)

</div>

## Sieć, DNS i VPN

<div class="grid cards" markdown>

-   :material-vpn: **WG Tunnel**
    
    ---
    
    Zaawansowany klient WireGuard dla Androida. Oferuje automatyczne tunelowanie, wiele profili oraz reguły split tunneling. Pozwala na wpięcie własnego szyfrowanego DNS (DoH).
    
    [➔ Przejdź do repozytorium](https://github.com/wgtunnel/android)

-   :material-cloud-lock: **Cloudflare WARP**
    
    ---
    
    Darmowy tunel oparty o WireGuard. Skutecznie ukrywa adres IP przed ISP i stronami, nie nakładając przy tym limitów transferu.
    
    !!! warning "Zbieranie metadanych"
        WARP nie jest usługą typu no-logs. Cloudflare zbiera metadane (ID instalacji, ilość danych, średnią prędkość) i podlega prawu USA. Sprawdza się jako wydajna warstwa szyfrująca przed ISP, ale nie zapewnia pełnej anonimowości.
    
    [➔ Przejdź do strony](https://1.1.1.1/)

-   :material-dns: **Quad9**
    
    ---
    
    Niezależny, bezpieczny resolver DNS. Automatycznie blokuje złośliwe domeny bez logowania adresu IP użytkownika.
    
    [➔ Przejdź do strony](https://quad9.net/)

-   :material-shield-lock: **Mullvad VPN**
    
    ---
    
    Złoty standard wśród płatnych VPN. Nie wymaga adresu e-mail (losowy numer konta) i oferuje w pełni audytowaną politykę braku logów.
    
    [➔ Przejdź do strony](https://mullvad.net/)

-   :material-shield-account: **IVPN**
    
    ---
    
    Audytowany dostawca VPN z obsługą protokołu WireGuard i Multi-Hop. Rejestracja odbywa się bez podawania danych osobowych.
    
    [➔ Przejdź do strony](https://www.ivpn.net/)

</div>

## Menedżery haseł i 2FA

<div class="grid cards" markdown>

-   :material-form-textbox-password: **KeePassDX**
    
    ---
    
    W pełni lokalny menedżer haseł. Zapewnia absolutną suwerenność danych bez polegania na zewnętrznych serwerach czy chmurze.
    
    [➔ Przejdź do repozytorium](https://github.com/Kunzisoft/KeePassDX)

-   :material-two-factor-authentication: **Aegis**
    
    ---
    
    Szyfrowana aplikacja do generowania kodów 2FA. Działa całkowicie offline, posiada opcję bezpiecznych kopii zapasowych.
    
    [➔ Przejdź do repozytorium](https://github.com/beemdevelopment/Aegis)

-   :material-shield-key: **Ente Auth**
    
    ---
    
    Wieloplatformowy authenticator wykorzystujący szyfrowanie end-to-end. Umożliwia bezpieczną synchronizację kodów między urządzeniami.
    
    [➔ Przejdź do repozytorium](https://github.com/ente/ente)

</div>

## Komunikacja i poczta

<div class="grid cards" markdown>

-   :material-message-lock: **Molly**
    
    ---
    
    Utwardzony fork Signala. Wspiera UnifiedPush (brak zależności od usług Google/FCM) oraz oferuje dodatkowe szyfrowanie lokalnej bazy danych.
    
    !!! warning "Opóźnienia aktualizacji"
        Jako fork, Molly może otrzymywać łatki bezpieczeństwa z kilkudniowym opóźnieniem względem oryginału. Mimo to, ze względu na niezależność od Google, to najlepszy wybór na GrapheneOS.
    
    [➔ Przejdź do repozytorium](https://github.com/mollyim/mollyim-android)

-   :material-email-check: **Tuta Mail**
    
    ---
    
    Kompleksowo szyfrowana poczta e-mail (model Zero Knowledge). W przeciwieństwie do wielu konkurentów, nie wykorzystuje bibliotek Google (Firebase) w wersji F-Droid.
    
    !!! warning "Wybór wersji"
        Wersja z GitHuba łączy się z `firebaselogging.googleapis.com` (z powodu Google Play Billing). **Instaluj wyłącznie wydanie z F-Droid**, które jest wolne od tych zależności.
    
    [➔ Przejdź do strony](https://tuta.com/)

-   :material-email-lock: **Proton Mail**
    
    ---
    
    Poczta oferująca szyfrowanie end-to-end i ochronę przed trackerami. Aplikacja na Androida jest open source (GPLv3).
    
    !!! warning "Higiena metadanych"
        Gotowe paczki APK oraz wersja z Google Play zawierają biblioteki Google (Firebase) i Sentry. Wyłączenie Sentry jest możliwe wyłącznie poprzez samodzielną kompilację ze źródeł. Jeśli nie kompilujesz aplikacji samodzielnie, musisz zaakceptować obecność tych bibliotek jako świadomy kompromis.
    
    [➔ Przejdź do repozytorium](https://github.com/ProtonMail/android-mail)

-   :material-email-lock: **Addy.io**
    
    ---
    
    W pełni otwarty i niezależny menedżer aliasów pocztowych. Skutecznie izoluje główną skrzynkę odbiorczą przed spamem i profilowaniem behawioralnym.
    
    [➔ Przejdź do repozytorium](https://github.com/anonaddy/addy-android)

</div>

## Notatki i organizacja

<div class="grid cards" markdown>

-   :material-note-text: **Markor**
    
    ---
    
    Lekki edytor czystego tekstu. Działa w pełni offline, nie posiada uprawnień sieciowych, a pliki zapisuje bezpośrednio w pamięci urządzenia.
    
    [➔ Przejdź do repozytorium](https://github.com/gsantner/markor)

-   :material-notebook-edit: **Notesnook**
    
    ---
    
    Szyfrowany end-to-end menedżer notatek z trybem offline. Pozwala zachować pełną kontrolę nad danymi i chroni przed analityką.
    
    [➔ Przejdź do repozytorium](https://github.com/streetwriters/notesnook)

-   :material-note-edit: **Open Notes**
    
    ---
    
    Minimalistyczny notatnik oferujący renderowanie Markdown i szyfrowane kopie zapasowe bez zbędnych uprawnień systemowych. Działa w 100% offline.
    
    !!! info "Status rozwoju"
        Ostatnia istotna aktualizacja miała miejsce w październiku 2026. Projekt jest aktywny, choć rozwijany w spokojnym tempie.
    
    [➔ Przejdź do repozytorium](https://github.com/Fandroid745/Open-notes)

</div>

## Galerie i edycja zdjęć

<div class="grid cards" markdown>

-   :material-image-lock: **Ente Photos**
    
    ---
    
    Alternatywa dla rozwiązań komercyjnych oferująca bezpieczne przechowywanie multimediów w chmurze z szyfrowaniem end-to-end.
    
    [➔ Przejdź do repozytorium](https://github.com/ente-io/ente)

-   :material-image-multiple: **Iris Gallery**
    
    ---
    
    Szybka, w pełni offline galeria zdjęć z wbudowanym edytorem i prywatnym sejfem.
    
    !!! success "W 100% offline"
        Manifest nie żąda uprawnienia INTERNET, a audyty Exodus Privacy nie wykryły żadnych trackerów.
    
    [➔ Przejdź do repozytorium](https://github.com/MohamadOday/iris-gallery)

-   :material-image-multiple: **ReFra**
    
    ---
    
    Nowoczesna i szybka galeria zdjęć z wydajnym wariantem funkcjonującym całkowicie bez uprawnień sieciowych.
    
    !!! info "Wybór wariantu"
        Domyślna wersja zawiera funkcje online i uprawnienie INTERNET. Aby uzyskać w pełni offline'owy odpowiednik, wybierz wariant `offline` z wydania na GitHubie.
    
    [➔ Przejdź do repozytorium](https://github.com/IacobIonut01/ReFra)

-   :material-image-edit: **Image Toolbox**
    
    ---
    
    Wielofunkcyjny edytor obrazów działający w pełni lokalnie. Umożliwia zaawansowaną edycję oraz bezpieczne wycinanie metadanych.
    
    !!! warning "Uprawnienie sieciowe"
        Mimo że aplikacja reklamowana jest jako offline, manifest zawiera uprawnienie INTERNET (prawdopodobnie do pobierania modeli AI). Jeśli chcesz mieć pewność, że aplikacja nie łączy się z siecią, zablokuj jej dostęp przez firewall systemowy.
    
    [➔ Przejdź do repozytorium](https://github.com/T8RIN/ImageToolbox)

</div>

## Multimedia

<div class="grid cards" markdown>

-   :material-youtube-tv: **PipePipe**
    
    ---
    
    Rozbudowany fork NewPipe. Skutecznie omija algorytmy YouTube i natywnie blokuje segmenty sponsorowane w filmach.
    
    !!! warning "Wykryty tracker"
        Audyt Exodus Privacy wykrył w aplikacji jeden tracker. Mimo to pozostaje jednym z najlepszych klientów YouTube pod kątem funkcji i blokowania reklam.
    
    [➔ Przejdź do repozytorium](https://github.com/InfinityLoop1308/PipePipe)

-   :material-music-circle: **Flow**
    
    ---
    
    Nowoczesny odtwarzacz wideo i audio z w pełni lokalnym silnikiem rekomendacji (FlowNeuro), który nie wysyła danych do chmury.
    
    [➔ Przejdź do repozytorium](https://github.com/a-edev/Flow)

-   :material-download-lock: **Seal**
    
    ---
    
    Prosty i skuteczny downloader (oparty na yt-dlp) do zapisywania materiałów z sieci na pamięć urządzenia.
    
    [➔ Przejdź do repozytorium](https://github.com/JunkFood02/Seal)

</div>

## Przechowywanie danych i chmura

<div class="grid cards" markdown>

-   :material-cloud-lock: **Filen**
    
    ---
    
    Klient chmury oferujący rygorystyczne szyfrowanie end-to-end z architekturą Zero Knowledge.
    
    !!! info "Historia trackerów"
        Starsze wersje aplikacji zawierały Sentry i Firebase Analytics. Najnowsze wydania (4.0.x) są według Exodus Privacy wolne od znanych trackerów. Zawsze korzystaj z najnowszego wydania.
    
    [➔ Przejdź do repozytorium](https://github.com/FilenCloudDienste/filen-ts)

-   :material-cloud-upload: **Proton Drive**
    
    ---
    
    Szyfrowana chmura z architekturą Zero Knowledge. Umożliwia bezpieczne przechowywanie i udostępnianie plików.
    
    !!! warning "Zależności zewnętrzne"
        Podobnie jak Proton Mail, oficjalne wydania zawierają biblioteki Firebase i Sentry. Jeśli zależy Ci na 100% czystym środowisku, wymaga to samodzielnej kompilacji lub wyboru innego klienta.
    
    [➔ Przejdź do repozytorium](https://github.com/ProtonDriveApps/android-drive)

</div>

## System i narzędzia

<div class="grid cards" markdown>

-   :material-keyboard-variant: **HeliBoard**
    
    ---
    
    W pełni konfigurowalna klawiatura ekranowa. Nigdy nie łączy się z siecią, co gwarantuje, że wpisywane hasła i dane nie wyciekną.
    
    [➔ Przejdź do repozytorium](https://github.com/HeliBorg/HeliBoard)

-   :material-map-marker-path: **CoMaps**
    
    ---
    
    Prywatna nawigacja offline oparta na OpenStreetMap. Działa bez trackerów i nie wymaga zakładania konta.
    
    [➔ Przejdź do repozytorium](https://github.com/comaps/comaps)

</div>
