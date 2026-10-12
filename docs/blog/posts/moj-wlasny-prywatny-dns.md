---
date: 2026-10-12
title: Mój własny, prywatny DNS. Po co?
description: Zbudowałem własny resolver DNS, który blokuje reklamy, trackery, malware i phishing. Bez panelu, bez logów, bez kompromisów.
categories:
  - Prywatność
  - DNS
tags:
  - dns
  - privacy
  - no-logs
  - self-hosted
authors:
  - Eteryu
---

Kiedyś używałem publicznego DNS z filtrowaniem. Działał dobrze. Blokował większość reklam, trackerów i tego całego śmiecia, który ciągnie się za każdą stroną. Ale zawsze brakowało mi jednej rzeczy: kontroli.

Nie nad tym, jakie domeny trafiają na listy. One i tak pochodzą od tych samych ludzi, którzy tworzą listy dla publicznych resolverów. Różnica polega na tym, że sam decyduję, z których list korzystam, jak je łączę i co z nich wyciągam. Mogę dodać dowolną listę z internetu, nie tylko te, które ktoś uznał za godne dodania do swojego katalogu. I gdy czegoś nie chcę blokować, dodaję to do własnych wyjątków i następnego dnia jest już przepuszczane. Bez czekania, aż ktoś inny uzna, że to dobry pomysł.

<!-- more -->

To mnie uwierało. Nie z powodu paranoi, ale z poczucia, że oddaję kontrolę nad czymś fundamentalnym. Nad tym, jak moje urządzenia łączą się ze światem.

## Co to właściwie jest?

Zbudowałem swój własny serwer DNS. Stoi w chmurze, więc mam do niego dostęp z każdego miejsca na świecie. Filtruje ruch według list, które sam wybieram i sam układam.

Działa to tak. Moje urządzenia pytają mój serwer o adres jakiejś strony. Serwer sprawdza, czy ta domena jest na liście, którą przygotowałem. Jeśli jest, odpowiada „nie znam takiej strony". Jeśli nie ma jej na liście, przekazuje zapytanie dalej.

Blokuję reklamy, trackery, telemetrię, domeny malware i phishing. Korzystam z ośmiu źródeł, które sam wybrałem. Jedne skupiają się na reklamach, inne na trackerach, jeszcze inne na zagrożeniach. Każde z nich wnosi coś innego.

Warto dodać, że to działa na poziomie DNS. Nie blokuje reklam w YouTube ani elementów wewnątrz strony. Do tego potrzebny jest osobny content blocker w przeglądarce. Mój resolver jest pierwszą warstwą, nie jedyną.

## Jak łączę listy i usuwam duplikaty

Problem z wieloma źródłami jest taki, że często się nakładają. Ta sama domena może pojawić się w trzech, czterech, pięciu listach jednocześnie. Gdybym wrzucił wszystko do jednego worka bez czyszczenia, miałbym listę pełną powtórzeń, większą niż potrzeba i wolniejszą w działaniu.

Zamiast tego mój pipeline robi coś prostego. Zbiera wszystkie domeny ze wszystkich źródeł do jednego zbioru, który z definicji nie może zawierać duplikatów. Jeśli ta sama domena pojawi się pięć razy, będzie tylko raz.

Po zebraniu wszystkich domen usuwam redundantne subdomeny. Jeśli na liście jest `example.com`, nie ma sensu trzymać na niej także `ads.example.com` i `track.example.com`. Każda z tych subdomen zostanie zablokowana, jeśli zablokowana jest domena nadrzędna. Usuwam je. Lista staje się mniejsza, a blokada działa tak samo.

Efekt jest taki, że z kilkudziesięciu tysięcy wpisów ze wszystkich źródeł zostaje jedna, czysta lista. Bez duplikatów. Bez zbędnych subdomen. Tylko to, co faktycznie blokuje coś, czego nie chcę widzieć.

!!! note "Automatyzacja"
    Ten proces dzieje się raz dziennie. Ja nie muszę nic robić. Lista sama się aktualizuje, sama się czyści i sama trafia do mojego resolvera.

## Dlaczego to nie ma panelu ani statystyk?

Mój resolver nie ma panelu administracyjnego. Nie ma wykresów, nie ma listy ostatnich zapytań, nie ma licznika zablokowanych domen.

To celowa decyzja. Panel ze statystykami oznacza, że ktoś, nawet jeśli tylko ja, gdzieś te dane przechowuje. Lista ostatnich zapytań to nic innego jak historia tego, co robię w internecie. A ja nie chcę, żeby taka historia istniała w jakiejkolwiek formie.

Mój resolver przetwarza zapytanie, zwraca odpowiedź i zapomina. Nie zapisuje niczego i nie analizuje. Nie ma czego nie logować, bo nie ma gdzie logować.

## Dla kogo to jest

To rozwiązanie dla kogoś, kto ma kilka urządzeń i chce, żeby wszystkie filtrowały tak samo. Telefon, laptop, tablet, cokolwiek. Bez instalowania osobnych aplikacji na każdym z nich.

Dla kogoś, kto ceni prywatność i nie potrzebuje wykresów, żeby czuć, że coś działa.

Dla kogoś, kto chce sam decydować, co blokuje, i nie czekać, aż ktoś inny zrobi to za niego.

Jeśli zależy Ci na panelu i statystykach, inne rozwiązania zrobią to lepiej. Ale jeśli cenisz kontrolę i prywatność bardziej niż wygodę, to jest dokładnie to.
