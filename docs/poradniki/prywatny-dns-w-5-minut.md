---
title: "Jak skonfigurować prywatny DNS w 5 minut"
description: "Instrukcja konfiguracji prywatnego DNS na Androidzie i iOS. Zamiast domyślnego DNS operatora, który widzi każdą Twoją domenę, użyj szyfrowanego resolvera z filtrowaniem reklam i trackerów."
icon: lucide/network
---

Domyślne ustawienia DNS w Twoim telefonie przesyłają każde zapytanie jawnym tekstem do serwerów operatora. Operator widzi, jakie strony odwiedzasz, z jakich aplikacji korzystasz i kiedy. Zmiana na prywatny DNS to jedna z tych czynności, które zajmują kilka minut, a realnie zmieniają poziom Twojej prywatności.

Ten poradnik pokazuje, jak to skonfigurować. Jeśli chcesz najpierw zrozumieć, jak działa DNS i dlaczego domyślna konfiguracja jest problemem, zajrzyj do sekcji [Bezpieczny DNS](../fundamenty/bezpieczny-dns.md).

## Wybór dostawcy

Najprostsze rozwiązania to gotowe usługi chmurowe. Nie musisz nic stawiać, nie musisz utrzymywać serwera. Zakładasz konto, wybierasz poziom filtrowania, dostajesz unikalny adres, który wpisujesz w telefonie.

- **NextDNS** — najwięcej opcji. Możesz wybierać listy blokujące, tworzyć własne reguły, przeglądać logi (jeśli chcesz). Darmowy plan: 300 000 zapytań miesięcznie.
- **Control D** — darmowe gotowe presety, m.in. z listami Hagezi. Nie wymaga konta, jeśli używasz gotowego presetu.
- **AdGuard DNS** — prosty, bez konfiguracji. Blokuje reklamy, trackery i malware.

Dla większości użytkowników **NextDNS** to najlepszy wybór, bo daje kontrolę bez potrzeby utrzymywania infrastruktury. Jeśli nie chcesz się rejestrować, wybierz **Control D** z presetem Hagezi albo **AdGuard DNS**.

## Konfiguracja na Androidzie

W nowszych wersjach Androida (od wersji 9 wzwyż) system natywnie obsługuje szyfrowany DNS przez DoT. Nie musisz instalować żadnej dodatkowej aplikacji.

1. Otwórz **Ustawienia** systemowe.
2. Wejdź w **Sieć i internet** → **Prywatny DNS** (może być też w „Zaawansowane").
3. Wybierz opcję **Nazwa hosta dostawcy prywatnego DNS** zamiast „Automatyczna".
4. Wpisz adres serwera wygenerowany przez Twojego dostawcę. Przykłady:
   - NextDNS: `twoj-id.dns.nextdns.io`
   - Control D (Hagezi Pro Plus): `x-hagezi-proplus.freedns.controld.com`
   - AdGuard DNS: `dns.adguard-dns.com`
5. Zapisz zmiany.

System od tej chwili będzie używał tego resolvera dla wszystkich zapytań DNS, także w aplikacjach.

## Konfiguracja na iOS i macOS

Systemy Apple obsługują szyfrowany DNS przez profile konfiguracyjne. Nie potrzebujesz żadnej aplikacji.

1. Zaloguj się u swojego dostawcy (np. NextDNS).
2. Wygeneruj **profil konfiguracyjny** (plik `.mobileconfig`).
3. Pobierz plik na urządzenie.
4. Wejdź w **Ustawienia** → **Ogólne** → **VPN i zarządzanie urządzeniem**.
5. Zatwierdź instalację profilu.
6. Profil pojawi się jako aktywny w **Ustawienia** → **Ogólne** → **VPN i zarządzanie urządzeniem** → **Profil konfiguracji**.

Od tej chwili cały ruch DNS z urządzenia będzie szyfrowany.

## Weryfikacja

Po skonfigurowaniu warto sprawdzić, czy wszystko działa.

- **Test blokowania reklam:** wejdź na `https://adblock.turtlecute.org/`. Powinieneś zobaczyć wynik powyżej 90% zablokowanych reklam i trackerów (zależy od wybranych list).
- **Test wycieku DNS:** wejdź na `ipleak.net`. Sprawdź, czy resolver widoczny na stronie to ten, którego skonfigurowałeś. Jeśli pojawia się adres Twojego operatora, konfiguracja nie zadziałała.

## Co dalej

Po skonfigurowaniu prywatnego DNS na telefonie możesz rozważyć:
- Skonfigurowanie tego samego resolvera na routerze — ochroni wszystkie urządzenia w domu.
- Połączenie z VPN — jeśli używasz VPN, upewnij się, że DNS nie wycieka poza tunel.
- Wybór bardziej agresywnych list — jeśli chcesz blokować więcej, ale uważaj na fałszywe trafienia.
