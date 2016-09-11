---
title: Snoop – Wizualizacja drzewa obiektów
author: Marcin Biegała
type: post
date: 2014-03-02
url: /2014/03/02/snoop-wizualizacja-drzewa-obiektow-visual-tree/
post_views_count:
  - 1161
dsq_thread_id:
  - 2345608296
dsq_needs_sync:
  - 1
categories:
  - Code
  - Tools
tags:
  - WPF
  - XAML

---
<div class="bean-alert info">
  Jest to drugi z małej serii postów traktujących o wizualizacji drzewa obiektów w WPF.<br /> Poprzedni znajdziesz tu:<br /> <a title="Wizualizacja drzewa obiektów (Visual Tree)" href="https://blog.biegala.net/2014/02/08/xamlspy/">WPF Visualizer &#8211; Wizualizacja drzewa obiektów (Visual Tree)</a><br /> W kolejce czeka jeszcze XAMLSpy<br />
</div>

W [poprzednim poście][1] opowiedzieliśmy sobie nieco o funkcjonalności samego Visual Studio w kwestii wizualizacji drzewa obiektów WPF. Myślę, że nie pozostawiłem też cienia wątpliwości jak mało przydatna jest to funkcja.  
Dziś coś dużo bardziej użytecznego.

Panie i Panowie, oto Snoop

<p style="text-align: center;">
  <a href="https://blog.biegala.net/wp-content/uploads/2014/03/2014-03-02-13_02_05-Dodaj-nowy-wpis-‹-Marcin-Biegała-—-WordPress.png" rel="lightbox[100]"><img class="size-full wp-image-103 aligncenter" src="https://blog.biegala.net/wp-content/uploads/2014/03/2014-03-02-13_02_05-Dodaj-nowy-wpis-‹-Marcin-Biegała-—-WordPress.png" alt="Snoop" width="590" height="27" /></a>
</p>

<p style="text-align: left;">
  Jest to malutki program (cały katalog zajmuje mniej niż 1,3 MB) o wielki możliwościach. Zawsze mam go pod ręką i nie raz pomógł zrozumieć co się dzieje w układzie okna.<br /> Snoop zapoczątkował <a title="Pete Blois" href="http://blois.us/">Pete Blois</a>, jednak dziś jest to w pełni otwarty kod który możecie znaleźć na <a title="https://snoopwpf.codeplex.com/" href="https://snoopwpf.codeplex.com/">Codeplex</a> lub na <a title="https://github.com/cplotts/snoopwpf" href="https://github.com/cplotts/snoopwpf">GitHub</a> (&#8216;Team Snoop&#8217;, który w teorii zarządza kodem Snoop synchronizuje oba repozytoria) i mimo, że nie rozwijany od ponad roku, wciąż jest bardzo wartościowym narzędziem.
</p>

<p style="text-align: left;">
  Do sedna. Co możemy z tym zrobić ?
</p>

<p style="text-align: left;">
  Na potrzeby tego posta przygotowałem bardzo proste okienko, zawierające trzy pola tekstowe i przycisk:<br /> <a href="http://blog.biegala.net/wp-content/uploads/2014/03/2014-03-02-13_21_25-MainWindow.png" rel="lightbox[100]"><img class="alignnone size-full wp-image-106" src="https://blog.biegala.net/wp-content/uploads/2014/03/2014-03-02-13_21_25-MainWindow.png" alt="Snoop - SampleApp" width="416" height="186" srcset="https://blog.biegala.net/wp-content/uploads/2014/03/2014-03-02-13_21_25-MainWindow-300x134.png 300w, https://blog.biegala.net/wp-content/uploads/2014/03/2014-03-02-13_21_25-MainWindow.png 416w" sizes="(max-width: 416px) 100vw, 416px" /></a>
</p>

<p style="text-align: left;">
  Uruchamiamy Snoop i przeciągamy celownik znajdujący się obok przycisku lornetki na interesującą nas aplikację.<br /> Po chwili otworzy się nowe okienko zawierające pełną analizę drzewa naszego widoku.
</p>

<p style="text-align: left;">
  <!--more-->
</p>

<p style="text-align: left;">
  Co my tu mamy:<img class=" wp-image-107 alignright" src="https://blog.biegala.net/wp-content/uploads/2014/03/2014-03-02-13_25_02-MainWindow-Snoop.png" alt="Snoop - MainWindow" width="538" height="436" srcset="https://blog.biegala.net/wp-content/uploads/2014/03/2014-03-02-13_25_02-MainWindow-Snoop-300x243.png 300w, https://blog.biegala.net/wp-content/uploads/2014/03/2014-03-02-13_25_02-MainWindow-Snoop.png 747w" sizes="(max-width: 538px) 100vw, 538px" /><br /> &#8211; z lewej pełne drzewo obiektów widoku (z wyszukiwarką i podglądem po najechaniu kursorem myszy, możemy też wcisnąć Ctrl+Shift na klawiaturze i najechać na interesujący nas obiekt w oknie aplikacji)
</p>

<p style="text-align: left;">
  &#8211; zakładkę &#8216;Properties&#8217; prezentującą właściwości danego obiektu, pokazuje ona zmiany wartości innym kolorem, jak również <span style="text-decoration: underline;">pozwala zmieniać wartości w trakcie działania programu</span>
</p>

<p style="text-align: left;">
  &#8211; zakładka &#8216;DataContext&#8217; prezentuje dane związane z aktualnie zdefiniowanym obiektem kontekstu
</p>

<p style="text-align: left;">
  &#8211; zakładka &#8216;Events&#8217; jak można się domyślić pokazuje historię wywołań zdarzeń powiązanych z obiektem, jak również czy zostały obsłużone, czy nie
</p>

<p style="text-align: left;">
  &#8211; &#8216;Methods&#8217; pozwala sprawdzić jakie metody udostępnia dany element, <span style="text-decoration: underline;">jak również wywołać je</span>
</p>

<p style="text-align: left;">
  &#8211; no i na koniec wisienka na torcie, czyli najnowsza funkcjonalności Snoop, zakładka &#8216;Powershell&#8217;. Dzięki niej możecie wykorzystać komendy powershell&#8217;a do przeszukiwania i  interacji z elementami drzewa wizualnego WPF
</p>

<p style="text-align: left;">
  Oprócz widoku właściwości Snoop posiada również lupkę, jak i możliwość wyświetlania obiektów w pseudo 3D, czasami przydatne przy bardziej skomplikowanych układach kontrolek.
</p>

<p style="text-align: left;">
  Na koniec zostawiłem jeszcze jedną perełkę.<img class=" wp-image-110 alignright" src="https://blog.biegala.net/wp-content/uploads/2014/03/2014-03-02-13_45_53-MainWindow-Snoop.png" alt="Snoop - EventView" width="386" height="364" />Nie wiem czy zwróciliście uwagę, w stopce okna Snoop pokazuje aktualne elementy które otrzymały focus.<br /> Małe, a jak cieszy!
</p>

<p style="text-align: left;">
  Podsumowując.<br /> Uważam Snoop, jako &#8216;must-have&#8217; programisty pracującego z aplikacjami w WPF. Jest poręczny, stabilny, nie wymaga przerywania działania aplikacji.<br /> I w dodatku jest darmowy!
</p>

<p style="text-align: left;">
  Nie pozostaje mi nic innego jak rzec, &#8216;bierzcie i ściągajcie z tego wszyscy&#8217;!
</p>

<p style="text-align: left;">
  Do następnego razu!
</p>

&nbsp;

 [1]: http://blog.biegala.net/2014/02/08/xamlspy/ "Wizualizacja drzewa obiektów (Visual Tree)"