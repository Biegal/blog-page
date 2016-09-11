---
title: Use the Keyboard Luke!
author: Marcin Biegała
type: post
date: 2014-12-21
url: /2014/12/21/use-keyboard-luke/
post_views_count:
  - 293
dsq_thread_id:
  - 3346903395
categories:
  - Tools
tags:
  - Productivity
  - Tool

---
Mój problem z blogowaniem polega na tym, że jak tylko rozgryzę jakiś problem, mam wrażenie że wszyscy już to wiedzą i niewarto o tym pisać. Dziś post stosunkowo &#8216;błahy&#8217;, ale zauważyłem że jednak nie wszyscy znają poniższe aplikacje.  
Będzie zatem o aplikacjach, ale za to tematycznie. Jako, że przy pracy, każde oderwanie rąk od klawiatury uważam za swego rodzaju stratę czasu, staram się jak najwięcej rzeczy obsługiwać z poziomu klawiatury, także podzielę się z Wami kilkoma aplikacjami i rozszerzeniami, których sam używam w tym celu.  
<!--more-->

## FarManager & ConEmu

Jedną z podstawowych rzeczy jakich potrzebujemy jest możliwość poruszania się po systemie plików na naszym komputerze. Po tych wszystkich katalogach z kodami źródłowymi, zdjęciami z wakacji itd. Oczywiście w Windows mamy już narzędzie do tego pod postacią Eksploratora, ale o ile &#8216;da się&#8217; go obsługiwać klawiaturą, to do produktywności mu daleko.  
Nie wiem czy to dobrze czy źle, ale ja pamiętam jeszcze coś co nazywało się Norton Commander i było nieodłączną częścią każdego komputera z DOSem. Od tamtej pory powstało wiele podobnych aplikacji dla Windows, z których chyba najpopularniejszy dziś jest Total Commander. Ja sam dość długo korzystałem z TotalCommander&#8217;a (wciskając 1,2,3 na komendę ;), dopóki gdzieś w sieci nie trafiłem na [FarManager][1].  
Kod pochodzący oryginalnie z Rosji, to aplikacja nawiązująca wszystkimi szczegółami do czasów DOSa i Nortona. Na pierwszy rzut oka nawet trudno uwierzyć, że jest to współczesna aplikacja, a nie relikt odgrzebany na dyskietce 3,5 cala.  
Ale właśnie dzięki temu &#8216;ubogiemu&#8217; UI, FAR jest mega szybki jeśli chodzi o start czy przeglądanie katalogów, a do tego do bólu przejrzysty. Mamy standardowe dwa panele, na których możemy wyświetlać listę plików, podgląd atrybutów czy treści plików. Do tego linia poleceń pod ręką (czyli np. cały GIT dostępny od zaraz), edytor tekstowy z kolorowaniem składni, czy klient FTP.  
Do tego cała rzesza wtyczek.  
Wady ? Duża część forum po rosyjsku :)<a href="https://blog.biegala.net/wp-content/uploads/2014/12/ConEmuAero.png" rel="lightbox[266]"><img class="alignright size-medium wp-image-283" src="https://blog.biegala.net/wp-content/uploads/2014/12/ConEmuAero-300x210.png" alt="FarManager & ConEmu" width="300" height="210" srcset="https://blog.biegala.net/wp-content/uploads/2014/12/ConEmuAero-300x210.png 300w, https://blog.biegala.net/wp-content/uploads/2014/12/ConEmuAero.png 799w" sizes="(max-width: 300px) 100vw, 300px" /></a>

No dobra, ale nie wspomniałem jeszcze o [ConEmu][2]. Generalnie rzecz ujmując [ConEmu ][2]to emulator konsoli Windows. Dodaje m.in obsługę zakładek, płynną zmianę rozmiarów okna, czy całą paletę ustawień &#8216;kosmetyczny&#8217; (kolory, czcionki, przezroczystość).  
Co wyróżnia [ConEmu ][2]od innych emulatorów ? Pełne wsparcie dla [FarManager][1]. Autor [ConEmu ][2]przygotował wtyczkę do Far&#8217;a, która pozwala m.in na łatwe przeglądanie wyników działania aplikacji w konsoli, czy otwieranie edytora tekstowego Far jako nowej zakładki.

A teraz najlepsze &#8211; to wszystko i więcej jest za free. Zarówno [FarManager ][1]jak i [ConEmu ][2]są dostępne za darmo, a nawet mają otwarty kod źródłowy

## Find And Run Robot

Ok, wiemy już jak poruszać się po dysku, czas zrobić użytek z tych wszystkich aplikacji, które <img class="alignright size-medium wp-image-285" src="https://blog.biegala.net/wp-content/uploads/2014/12/farr_01-300x146.png" alt="FARR" width="300" height="146" srcset="https://blog.biegala.net/wp-content/uploads/2014/12/farr_01-300x146.png 300w, https://blog.biegala.net/wp-content/uploads/2014/12/farr_01.png 602w" sizes="(max-width: 300px) 100vw, 300px" />zainstalowaliśmy. Testowałem wiele programów tego typu, był i SlickRun i Launchy, i Executor, ale niewiedzieć czemu to właśnie [FARR ][3]zadomowił się na dłużej.  
[FARR ][3]ma wszystko czego można się spodziewać &#8211; uruchamianie aplikacji, automatyczne indeksowanie, obsługę wtyczek itd. a do tego multum ustawień, zachowując przy tym szybkość działania.  
Nie twierdzę, że to najlepsza aplikacja tego typu, ale na pewno warta rozważenia.

## Switcheroo

Czas na powód całego tego posta &#8211; [Switcheroo][4] &#8211; mała apka, ale po zainstalowaniu zastanawiałem się jak działałem bez niej. [Switcheroo ][4]służy tylko i wyłącznie do jednej rzeczy, do przełączanie się między aplikacjami (jak alt+tab), ale za to robi to dobrze :)  
Całą zabawa polega na tym, że [Switcheroo ][4]pozwala na wyszukiwanie po nazwie aplikacji i okna, więc nawet jeśli mamy otwartych ich sporo, kilka klawiszy i mamy co chcemy :)

## Vimium

Wiemy już jak poruszać się po systemie, ale nie da się zaprzeczyć, że w dobie internetu, część naszego dnia spędzamy gapiąc się w okno przeglądarki. Co prawda przeglądarki radzą sobie z obsługą za pomocą klawiatury, jedne robią to lepiej, inne gorzej, ale i tak, żadna nie może się równać z tym co proponuje [Vimium][5]. Jest to wtyczka do Chrome, która jak można się domyślić czerpie inspirację z Vi. Cała zabawa polega na tym, że po wciśnieciu odpowiedniego klawisza, każdy z odnośników na stronie dostaje etykietkę z kolejnym klawiszem &#8211; wciskając go przejdziemy do wybranego odnośnika (lub otworzymy go w nowej zakładce). Do tego poruszanie się pomiędzy zakładkami, przeszukiwanie historii i bookmarków, słowem full service.  
Polecam!

## Shift+F10

Na koniec drobnostka. Ostatnio mam okazję pracować na laptopie Lenovo, który nie ma klawisza wywołującego menu <img class="alignright  wp-image-287" src="https://blog.biegala.net/wp-content/uploads/2014/12/sgzBP-300x192.jpg" alt="Klawisz menu kontekstowe" width="216" height="138" />kontekstowe. Do tego momentu, nie zdawałem sobie sprawy jak często go używam. Chwila grzebania w sieci i okazało się, że to samo można osiągnąć kombinacją klawiszy Shift+F10. Co prawda nie działa wszędzie, ale czasem ratuje sytuacje.

To tyle na dziś.  
Chętnie poczytam jakich Wy aplikacji używacie, żeby zapewnić sobie produktywność.

 [1]: http://www.farmanager.com/
 [2]: https://code.google.com/p/conemu-maximus5/
 [3]: http://www.donationcoder.com/Software/Mouser/findrun/
 [4]: http://www.switcheroo.io/
 [5]: http://vimium.github.io/