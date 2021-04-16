---
title: Brak możliwości logowania do SQLServer
author: Marcin Biegała
type: post
date: 2014-11-17
url: /2014/11/17/brak-mozliwosci-logowania-do-sqlserver/
post_views_count:
  - 357
  - 357
dsq_thread_id:
  - 3362077731
categories:
  - Code
  - Tools
tags:
  - SQL

---
Szczerze, myślałem że taka sytuacja jest niemożliwa. Ale, że sam siebie wpakuje w takie bagno, to już mogłem się spodziewać.<img class="alignright wp-image-245" src="https://miedzy-nawiasami.pl/wp-content/uploads/2014/11/gold-2480_640.jpg" alt="Brak możliwości logowania do SQLServer" width="253" height="189" srcset="https://miedzy-nawiasami.pl/wp-content/uploads/2014/11/gold-2480_640-300x224.jpg 300w, https://miedzy-nawiasami.pl/wp-content/uploads/2014/11/gold-2480_640.jpg 640w" sizes="(max-width: 253px) 100vw, 253px" />

Otóż, nie wiem czy wszyscy zdają sobie sprawę, ale można mieć instancję SQL Server (w tym przypadku Express), do której nie można się zalogować :)
Jak można już wywnioskować nie jestem bazodanowym magiem, ba nawet czeladnikiem nie jestem. Próbując wyłączyć dostęp do bazy przez Windows Integrated Login, skończyłem z serwerem do którego zalogować się nie sposób (użytkownikom windowsowym odebrałem prawo, a jak się okazało sa go nie miał&#8230;).
No to klops myślę. Niby to nie była baza produkcyjna, ale i tak danych szkoda, czasu szkoda. No i tak reinstalować od razu ? Tak bez walki ?

Okazało się, że jest rozwiązanie takiego impasu. I to stosunkowo proste.<!--more-->

Otóż w 99,9% przypadków, nasz SQLServer będzie działał jako serwis Windows. Ale zapominamy, że jest tam też zwykły plik wykonywalny .exe. Ba, nawet potrafi przyjmować parametry!
A to już brzmi jak początek czegoś dobrego.

Zatrzymujemy zatem nasz serwis SQLServer (np. poprzez panel services.msc).

Odszukujemy plik sqlservr.exe (W ścieżce podobnej do C:\Program Files\Microsoft SQL Server\MSSQL11.SQLEXPRESS\MSSQL\Binn) i uruchamiamy:

<span style="font-weight: bold; color: #000000;">sqlservr.exe -m</span>

i czekamy, aż logi w konsoli się przewiną, ukazując komunikat, że SQLServer jest gotowy na połączenia.

Parametr &#8216;-m&#8217; oznacza &#8216;Single User Mode&#8217;. Co to daje ? Otóż pierwsze (i jedyne, więc trzeba się spieszyć ;) połączenie automatycznie dostaje prawa administratora. Możemy zatem naprawić nasze błędy (czy to przez SSMS, czy SQLCmd), a następnie zamknąć serwer (polecenie SHUTDOWN) i przywrócić nasz oryginalny serwis.

Prosto i przyjemnie!

Chciałem przy okazji też wspomnieć o bezpieczeństwie w tym przypadku. Często w małych firmach, serwer SQL nie ma dedykowanej maszyny i chodzi na tym samym komputerze, na którym wykonywana jest codzienna praca. Pamiętajmy o tym, aby odpowiednio zabezpieczyć konta użytkowników (nie każdy potrzebuje konto administratora, żeby korzystać z Outlooka i CRM ;) ), bo możemy się zdziwić i znaleźć nasze dane u konkurencji.