---
title: GIT i znak komentarza
author: Marcin Biegała
type: post
date: 2015-04-11
url: /2015/04/11/git-i-znak-komentarza/
post_views_count:
  - 205
dsq_thread_id:
  - 3673630596
categories:
  - Tools
tags:
  - GIT
  - Tool

---
Mam taką wadę, że generalnie lubię porządek. Lubię jak wszystko ma swoje miejsce i wiem gdzie tego szukać.  
Podobnie mam z kodem w repozytorium, nie lubię tam bałaganu. Dlatego też jedną z praktyk, które stosuje już od dawna jest wpisywanie identyfikatora zadania w treść &#8216;commit message&#8217;.  
Polecam takie podejście, ponieważ bardzo ułatwia odbudowanie kontekstu całej zmiany po jakimś czasie (szybko znajdziemy odpowiednie zadanie czy historyjkę użytkownika, sprawdzimy co było źródłem zmiany itp. itd.).

<!--more-->I teraz pewnie się zastanawiacie, co to ma wspólnego z GITem ? Otóż każdy system zarządzania zadaniami, czy to Mantis, czy to JIRA, czy VersionOne, ma jakiś swój schemat nadawania identyfikatorów zadań. W swoich projektach często wykorzystuję 

[Redmine][1] do zarządzania bug&#8217;ami i zadaniami. Ten jako identyfikatorów używa liczb całkowitych, moje commity rozpoczynają się wiec od np:  
#297:..  
#457:&#8230;.

Jeśli wciąż nie widzicie nadchodzących problemów, to przypomnę że domyślnym znakiem komentarza dla GIT jest &#8216;#&#8217; :)  
Aplikacje do GIT z których korzystałem (typu TortoiseGIT np.) radzą sobie z tym problemem i bez skrępowania możemy zaczynać nasze opisy od #. Gorzej jeśli tak jak ja wolicie konsolę. Zwykłe <span class="lang:batch decode:true crayon-inline">git commit</span>  które otwiera nam domyślny edytor do wpisania opisu zmian już stawia problemy i nie przyjmuje wiadomości zaczynających się od #.  
To natomiast da się dość łatwo ominąć stosując przełącznik -m:

<pre class="toolbar:0 lang:batch decode:true ">git commit -m "#234: Fixing null pointer exception"</pre>

Ale takie podejście odrobinę nas ogranicza i utrudnia wprowadzanie dłuższych opisów zawierających wiele linii.

Okazuje się, że GIT od wersji [1.8.2][2] zawiera pewne udogodnienie, które rozwiązuje nam powyższy problem: parametr <span class="lang:batch decode:true  crayon-inline ">core.commentchar</span>

Pokazuję i objaśniam.  
Wersja domyślna:

<pre class="lang:vim decode:true">#234: Fixing null pointer exception 

# Please enter the commit message for your changes. Lines starting 
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master 
# 
# Initial commit 
# 
# Changes to be committed: 
# new file: test.txt 
#</pre>

Zmieniamy wspomniane ustawienie: <span class="lang:batch decode:true  crayon-inline ">git config core.commentchar ~</span>

I voila:

<pre class="lang:vim decode:true ">#234: Fixing null pointer exception 

~ Please enter the commit message for your changes. Lines starting 
~ with '~' will be ignored, and an empty message aborts the commit.
~ On branch master 
~ 
~ Initial commit 
~ 
~ Changes to be committed: 
~ new file: test.txt 
~</pre>

Możemy już bezproblemu korzystać z # w naszych opisach commitów nie wychodząc z konsoli.

I nastał ład i porządek!

&nbsp;

 [1]: http://www.redmine.org/ "Redmine"
 [2]: http://article.gmane.org/gmane.linux.kernel/1443021 "GIT 1.8.2"