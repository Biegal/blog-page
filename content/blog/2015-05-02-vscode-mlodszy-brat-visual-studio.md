---
title: VSCode – Młodszy brat Visual Studio
author: Marcin Biegała
type: post
date: 2015-05-02
url: /2015/05/02/vscode-mlodszy-brat-visual-studio/
post_views_count:
  - 218
dsq_thread_id:
  - 3730092558
categories:
  - NoCode
  - Tools
tags:
  - CSharp
  - GIT
  - Tool

---
29 kwietnia, na konferencji Build 2015 Microsoft zaskoczył prawie wszystkich wypuszczając na świat nowy twór: [VisualStudio CODE][1]. Bardzo prosty, lecz działający edytor kodu, który (\*werble\*) od ręki działa na Linuxie i MacOsX!
Lekko oszukali, bo całość opiera się na projektach [Chromium ][2]i [Electron][3], ale już sam fakt, że bez kombinowania mamy dostęp do wersji na platformy inne niż Windows pokazuje, że w Microsoft naprawdę coś zaczyna się zmieniać.

Co owy edytor potrafi ? Otóż otrzymujemy (pomijając oczywiste jak kolorowanie składni):<a href="https://miedzy-nawiasami.pl/wp-content/uploads/2015/05/hero-osx-e1430561425932.png" rel="lightbox[396]"><img class="alignright wp-image-397 size-medium" src="https://miedzy-nawiasami.pl/wp-content/uploads/2015/05/hero-osx-300x199.png" alt="VSCode" width="300" height="199" /></a>
&#8211; intellisense, czyli podpowiadanie kodu dla .net i JS
&#8211; nawigację w kodzie (przejdź do definicji, znajdź odwołania itp)
&#8211; integrację z GITem
&#8211; debugger (znów i dla .net i dla Node.js)

Prawda jest taka, że to produkt w bardzo wczesnej fazie rozwoju i daleko ma do tak już zakorzenionych w rynku edytorów jak SublimeText czy Brackets, ale chociażby ze względu na debugger, może być ciekawym uzupełnieniem naszego zestawu narzędzi. Zobaczymy w którą stronę MS pójdzie i czy uda się utrzymać ten edytor w obecnej, lekkiej formie, czy znów po kilku wersjach będzie ociężałym kombajnem pokroju w stylu starszego brata.

<!--more-->Osobiście bardzo mi się pomysł takiego &#8216;restartu&#8217; podoba i z chęcią porzuciłbym ogromniastego VisualStudio, na rzecz niedużego nowoczesnego edytora. Osobiście, z reguły nie mam potrzeby korzystania z wszystkich &#8216;enterprise&#8217; funkcjonalności w VS, jak diagramy UMLopodobne, integracje z bazami danych, TFSami itp. Wolałbym lekkie, szybkie środowisko, które działa i nie marnuje mi czasu :)

PS: Gdy po raz pierwszy o nim przeczytałem, pierwsze co przyszło mi do głowy, to czemuż ach czemuż nie mogli się skupić na otwartym [Omnisharpie][4], a temat samego edytora zostawić innym? Ale po odrobinie googlania, okazało się że VSCode korzysta właśnie z Omnisharp pod spodem, a w wyniku prac nad nowym narzędziem sporo pull requestów zostało wysłanych z powrotem do wtyczki.
Także to plus wsparcie dla debuggowania i okazuje się, że wcale VSCode nie jest skazany na porażkę :)

 [1]: https://code.visualstudio.com/
 [2]: https://www.chromium.org/Home
 [3]: http://electron.atom.io/
 [4]: http://www.omnisharp.net/