---
title: "Go 1.13 - na to czekałem!"
url: "blog/go-113-na-to-czekalem"
author: Marcin Biegała
type: post
tags: [golang]
categories:
  - code
  - golang
date: 2019-09-09T06:20:21+01:00
---

Parę dni temu otrzymaliśmy kolejną wersję golang. Tym razem 1.13.  
Jak zwykle, dostaliśmy szereg raczej mniejszych poprawek, wszystko wg. ideologii
małych kroków.  
Ta wersja ma jednak długo oczekiwaną przeze mnie zmianę.  
GOMODULES staje się domyślnym podejściem!

{{< img-post path="/img/" file="gologo.png" alt="Golang logo" type="right" >}}

Wracając do początku. Oryginalnie golang opierał swoje działanie i narzędzia na strukturze katalogów i ich położeniu względem GOPATH, specjalnie określonej ścieżki na dysku.  
Jest to kwestia subiektywna, ale strasznie mnie to irytowało, bo zawsze dzieliłem projekty raczej ze względu na klientów itp. raczej niż na technologię. Tu musiałem wszyskie projekty trzymać w jednym katalogu.  
Ten wymóg był podyktowany nie tylko narzędziami do budowania, ale także organizacją zależności i bibliotek, która
od samego początku w Go odstawałą od 'dzisiejszych standardów'. Twórcy Go obserwowali narzędzia, które tworzyła społeczność i zbierając doświadczenia i opinie stworzyli coś własnego - go modules.  
Nie tylko Go doczekało się wreszcie porządnego systemu do zarządzania zależnościami, ale też uwolniło się od GOPATH. Go modules radzie sobie z każdym miejscem na dysku, projekty mogą leżeć tam gdzie NAM się podoba.

Co to ma konkretnie wspólnego z wersją 1.13?  
Otóż go modules działało już od jakiegoś czasu, ale w opcji 'opt in'. Musieliśmy wyraźnie powiedzieć, że chcemy tego używać. Od wersji 1.13 Go domyślnie będzie używać go modules, nawet jeśli projekt jest wewnątrz gopath.
Dla mnie to drobna, ale wyczekiwana zmiana!

Inne ciekawe punkty tej wersji to moim zdaniem:  
- możliwość 'owijania' (wrap) błędów, co pozwoli nam tworzyć bogatszy kontekst dla sytuacji wyjątkowych (mamy też nowe funkcje `errors.Unwrap`, `errors.Is` i `errors.As`)  
- paczka `database/sql` dostała dwa nowe typy: `NullTime` i `NullInt32`  
- wsparcie dla TLS 1.3


Więcej szczegółów możecie przeczytać [oficjalnej dokumentacji](https://golang.org/doc/go1.13)
