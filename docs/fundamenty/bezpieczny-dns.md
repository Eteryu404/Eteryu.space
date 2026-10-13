---
title: Bezpieczny DNS
description: Jak działa DNS, dlaczego domyślna konfiguracja operatora to luka w prywatności, i jak działają mechanizmy obronne prywatnego DNS.
icon: lucide/server
---

# Filtrowanie ruchu na poziomie DNS

!!! abstract "Cel artykułu"
    Ten materiał wyjaśnia mechanikę działania protokołu DNS oraz zagrożenia wynikające z domyślnej konfiguracji narzucanej przez operatorów.
    
    Jeśli szukasz konkretnych instrukcji konfiguracji, zajrzyj do poradnika [Jak skonfigurować prywatny DNS](../poradniki/prywatny-dns-w-5-minut.md).

Zmiana serwerów DNS to absolutny fundament cyfrowej higieny i pierwszy krok do zabezpieczenia urządzenia przed większością realnych zagrożeń. Zobaczmy, co dokładnie dzieje się pod maską Twojego telefonu lub komputera, gdy wpisujesz adres strony internetowej, i dlaczego przejęcie kontroli nad tym procesem to Twoja najważniejsza tarcza obronna.

## Mechanika działania protokołu DNS

Protokół DNS, czyli system nazw domenowych, to w uproszczeniu internetowa książka adresowa. Ty zapamiętujesz przyjazne i łatwe do wymówienia nazwy witryn, ale komputery oraz routery komunikują się ze sobą wyłącznie za pomocą ciągów cyfr, czyli adresów IP.

Kiedy wpisujesz w przeglądarce adres bloga, Twoje urządzenie nie ma pojęcia, gdzie fizycznie znajduje się serwer. Musi najpierw wysłać zapytanie w świat i zapytać o konkretny numer docelowy. Wyobraź sobie wyspecjalizowany serwer DNS jako Twojego osobistego asystenta:

1. **Pamięć podręczna.** Asystent zagląda do podręcznego notatnika w systemie. Jeśli niedawno pytałeś o tę stronę, adres jest gotowy do podania.
2. **Główna centrala.** Asystent udaje się do głównych zarządców internetu, którzy kierują go do odpowiedniej strefy.
3. **Kierownik strefy.** Serwer zarządzający końcówkami takimi jak `.pl` lub `.net` podaje namiary na rejestratora.
4. **Właściwe źródło.** Asystent dociera do autorytatywnego serwera, który wydaje ostateczny adres IP.
5. **Powrót z adresem.** Asystent wraca do przeglądarki z ciągiem cyfr, a Ty widzisz poprawnie załadowaną witrynę.

## Zagrożenia wynikające z domyślnej konfiguracji

Po wyjęciu smartfona z pudełka urządzenie domyślnie korzysta z serwerów przydzielonych przez dostawcę internetu. To ogromna luka w prywatności.

Twój operator dokładnie widzi, o jakie adresy pyta urządzenie. Zna całą historię zapytań systemowych, wie, kiedy korzystasz z aplikacji bankowej i jakie serwisy odwiedzasz. Co gorsza, klasyczne zapytania przesyłane są jawnym tekstem. Nawet jeśli strona jest w pełni zabezpieczona kłódką szyfrowania, każdy punkt pośredniczący doskonale widzi, z jaką domeną próbujesz nawiązać połączenie. To czyste profilowanie behawioralne.

## Prywatny DNS i mechanizmy obronne

Odzyskanie kontroli polega na zmianie domyślnego asystenta na wysoce zaufanego dostawcę, który wprowadza dwa potężne mechanizmy obronne.

!!! info "Szyfrowana koperta (DoH oraz DoT)"
    Twój nowy dostawca umieszcza wszystkie zapytania wychodzące z telefonu w zaszyfrowanym tunelu. Tryb prywatny opiera się na standardzie DNS over TLS lub DNS over HTTPS. Dostawca internetu widzi jedynie sam fakt łączenia się z bezpiecznym serwerem, tracąc wgląd w to, o jakie domeny pyta system.

!!! success "Cyfrowa czarna dziura (Sinkholing)"
    Serwer posiada wbudowane i nieustannie aktualizowane listy zagrożeń. Kiedy aplikacja działająca w tle próbuje wysłać dane do serwera śledzącego, zaufany serwer blokuje zapytanie. Wraca do aplikacji i zwraca tak zwany pusty pakiet. Szkodliwe skrypty uderzają w próżnię, reklamy się nie ładują, a telemetria pozostaje bezpiecznie na urządzeniu.

## Jak to skonfigurować?

Instrukcje konfiguracji dla Androida, iOS i macOS znajdziesz w poradniku [Jak skonfigurować prywatny DNS w 5 minut](../poradniki/prywatny-dns-w-5-minut.md).
