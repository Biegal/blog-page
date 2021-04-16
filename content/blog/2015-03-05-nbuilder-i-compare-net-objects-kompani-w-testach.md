---
title: NBuilder i Compare .Net Objects – kompani w testach
author: Marcin Biegała
type: post
date: 2015-03-05
url: /2015/03/05/nbuilder-i-compare-net-objects-kompani-w-testach/
post_views_count:
  - 183
dsq_thread_id:
  - 3569949523
categories:
  - Code
  - Unit Tests
tags:
  - CSharp
  - Lib

---
Dziś wreszcie pojawi się trochę kodu :)
Mam nadzieję, że o zyskach przy okazji pisania testów jednostkowych, czy stosowaniu TDD nie muszę pisać. Jednak te z reguły możemy docenić dopiero w dłuższej perspektywie pracy z projektem. Tu i teraz, w chwili pisania kodu, nie oszukujmy się &#8211; jest to dodatkowa praca.
Ale nawet jeśli staramy się trzymać dobrych praktyk, zasad SOLID, a nasze metody są krótkie i przemyślane, zdarzają się projekty gdzie operujemy na rozbudowanych modelach danych, z dużą ilością pól i właściwości.

To odbija się czkawką podczas pisania testów w dwojaki sposób:
&#8211; aby przetestować nasze metody, potrzebujemy model wypełniony danymi, już możemy sobie wyobrazić te kilka, kilkanaście linii kodu tylko po to, by odtworzyć pewien stan obiektu i przekazać go do naszej metody w teście
&#8211; potrzebujemy porównać czy nasze modele są sobie równe, w rozumieniu że wszystkie ich właściwości są sobie równe.
Oba problemy wydają się trywialne, ale w pewien sposób &#8216;zatruwają&#8217; nasz kod. Albo nasze testy rozrastają się o kilkanaście linijek nie związanych z &#8216;intencją&#8217; naszego testu, albo zaczynamy tworzyć całą strukturę, a wręcz framework do naszych testów jednostkowych, żeby w jakiś sposób wyekstrahować ten powtarzalny kod poza pliki testów.
Całość może się odbić negatywnie na naszym zaangażowaniu w testy, bo po prostu nie będzie nam się chciało pisać tego całego dodatkowego kodu, bo przecież zaraz kończę pracę, a sam kod aplikacji już napisałem.

Jak możemy sobie pomóc ? Otóż stosując dwie proste biblioteki: <a title="NBuilder" href="https://github.com/garethdown44/nbuilder/" target="_blank">NBuilder</a> i <a title="Compare .Net Objects" href="https://comparenetobjects.codeplex.com/" target="_blank">Compare .NET Objects</a>

<!--more-->NBuilder jak można się domyśleć, wspomaga nas w budowaniu obiektów.


Wyobraźmy sobie na wstępie, że w naszym kodzie mamy następującą klasę:

<pre class="lang:c# decode:true">public class Person
    {
        public int Id { get; set; }
        public string FirstName { get; set; }
        public string MiddleName { get; set; }
        public string LastName { get; set; }
        public string Email { get; set; }
        public string PhoneNumber { get; set; }
        public string AlternatePhoneNumber { get; set; }
        public string AddressStreet { get; set; }
        public string AddressCity { get; set; }
        public string AddressPostalCode { get; set; }
        public string AddressCountry { get; set; }
        public DateTime BirthDate { get; set; }
        public string TwitterHandle { get; set; }
        public string WebSiteAddress { get; set; }
        public DateTime RegistrationDate { get; set; }
        public Guid RegistrationToken { get; set; }
    }</pre>

Niby nic nadzwyczajnego, ale trochę tych właściwości ktoś wymyślił. My, zabieramy się za przetestowanie jakiegoś fragmentu kodu, który z tej klasy korzysta &#8211; np. podczas serializacji.
Przy jednym teście moglibyśmy się pokusić o przygotowanie takiego obiektu samemu. Przy drugim, już zaczniemy kombinować nad jakimiś metodami do generowania losowych tekstów itp., a przy piątym zbudujemy całą fabrykę takich testowych obiektów ;) Bo przecież można.

Można, ale nie trzeba, bo ktoś już za nas ten problem rozwiązał.
Zaczynamy od dodania do projektu [nuget NBuilder][1] i już możemy zbudować taki oto kod:

<pre class="lang:c# decode:true">var allRandom = Builder&lt;Person&gt;.CreateNew().Build();

            var listOfRandomPeople = Builder&lt;Person&gt;.CreateListOfSize(20).Build();

            var personWithSpecificId = Builder&lt;Person&gt;.CreateNew()
                                                        .With(x =&gt; x.Id = 666)
                                                        .With(x =&gt; x.FirstName = "Jaś")
                                                        .With(x =&gt; x.LastName = "Fasola")
                                                        .Build();

            var birthDate = DateTime.Now;
            var listWhereFirstTwoHasSameBirthDate = Builder&lt;Person&gt;.CreateListOfSize(26)
                                                    .TheFirst(2)
                                                        .With(x =&gt; x.BirthDate = birthDate)
                                                    .Build();

            var listWhereEveryoneHasSameName = Builder&lt;Person&gt;.CreateListOfSize(26)
                                                    .All()
                                                        .With(x =&gt; x.FirstName = "John")
                                                        .With(x =&gt; x.LastName = "Doe")
                                                    .Build();</pre>

Ciekawi co też pojawiło się jako wartości w naszych obiektach ? Proszę bardzo:

<a href="https://miedzy-nawiasami.pl/wp-content/uploads/2015/03/2015-03-02-21_27_41-master-•-NBuilderSample-Debug_Any-CPU-Debugging-Microsoft-Visual-Studio.png" rel="lightbox[313]"><img class="aligncenter wp-image-338 size-full" src="https://miedzy-nawiasami.pl/wp-content/uploads/2015/03/2015-03-02-21_27_41-master-•-NBuilderSample-Debug_Any-CPU-Debugging-Microsoft-Visual-Studio.png" alt="NBuilder i Compare .Net Objects - Zawartość obiektu z NBuilder" width="537" height="302" srcset="https://miedzy-nawiasami.pl/wp-content/uploads/2015/03/2015-03-02-21_27_41-master-•-NBuilderSample-Debug_Any-CPU-Debugging-Microsoft-Visual-Studio-300x169.png 300w, https://miedzy-nawiasami.pl/wp-content/uploads/2015/03/2015-03-02-21_27_41-master-•-NBuilderSample-Debug_Any-CPU-Debugging-Microsoft-Visual-Studio.png 537w" sizes="(max-width: 537px) 100vw, 537px" /></a>

Oczywiście to tylko fragment możliwości NBuilder. Możemy m.in wywoływać konkretne konstruktory, przekazywać do nich zadane parametry, wywoływać metody na wygenerowanych obiektach, a wszystko to ładnie schowane za &#8216;fluent api&#8217;.
I to zrobione za nas!

No to skoro już mamy gotowe obiekty do przetestowania naszego serializowania, przydałoby się sprawdzić, czy to co odczytaliśmy, jest dokładnie tym co chcieliśmy zapisać. I znów, moglibyśmy się pokusić o kawałek autorskiego kodu, który nam ten problem rozwiąże, ale wtedy nie przybliżyłbym Wam naszego drugiego bohatera, czyli biblioteki <a title="Compare .Net Objects" href="https://comparenetobjects.codeplex.com/" target="_blank">Compare .NET Objects</a>.
Dość gadania, niech kod sam przemówi:

<pre class="lang:c# decode:true">var people = Builder&lt;Person&gt;.CreateListOfSize(2)
                                        .TheFirst(1).With(x =&gt; x.FirstName = "Jo")
                                        .TheNext(1).With(x =&gt; x.FirstName = "Mary")
                                        .Build();

            var personJo = people[0];
            var personMary = people[1];

            var compareLogic = new CompareLogic();
            compareLogic.Config.MaxDifferences = Int32.MaxValue;

            var comparisonResultA = compareLogic.Compare(personJo, personMary);
            var comparisonResultB = compareLogic.Compare(personJo, personJo);

            Console.WriteLine("Result A [personJo vs personMary]: " + comparisonResultA.AreEqual);
            Console.WriteLine("Differences A [personJo vs personMary]: " + comparisonResultA.DifferencesString);

            Console.WriteLine();

            Console.WriteLine("Result B [personJo vs personJo]: " + comparisonResultB.AreEqual);
            Console.WriteLine("Differences B [personJo vs personJo]: " + comparisonResultB.DifferencesString);</pre>

<a href="https://miedzy-nawiasami.pl/wp-content/uploads/2015/03/ComnpareNetObjectsConsoleResult.png" rel="lightbox[313]"><img class="alignright wp-image-342 size-medium" src="https://miedzy-nawiasami.pl/wp-content/uploads/2015/03/ComnpareNetObjectsConsoleResult-283x300.png" alt="NBuilder i Compare .Net Objects - Wynik działania Compare .Net Objects" width="283" height="300" srcset="https://miedzy-nawiasami.pl/wp-content/uploads/2015/03/ComnpareNetObjectsConsoleResult-283x300.png 283w, https://miedzy-nawiasami.pl/wp-content/uploads/2015/03/ComnpareNetObjectsConsoleResult.png 813w" sizes="(max-width: 283px) 100vw, 283px" /></a> Po uruchomieniu, w konsoli otrzymamy zarówno stwierdzenie, czy oba obiekty są równe (true/false) jak również listę różnic (jakie pole i jakie wartości).
Co prawda wypisane wprost do konsoli nie wygląda zbyt klarownie, ale do dyspozycji mamy również odpowiednie obiekty, po których możemy sobie iterować w kodzie i zrobić z wartościami co nam się żywnie podoba.

Dodatkowo biblioteka posiada dość dużo opcji pozwalających nam wpłynąć na logikę porównywania. Możemy m.in określić ile różnic nas interesuje (w przykładzie użyłem Int32.MaxValue, żeby pokazać wszystkie różnice, ale równie dobrze możemy zatrzymać się na pierwszej), czy chcemy porównywać prywatne i statyczne pola, możemy też podpiąć własny komparator, lub po prostu zignorować część właściwości.

Co prawda przedstawione biblioteki nie wystrzelą rakiety w kosmos, nie wyleczą nikogo z raka, ani nie zredukują bezrobocia, ale są to jedne z tych narzędzi, które przewijają się w większości projektów, w których biorę udział. Bo kto kiedyś nie próbował np. zautomatyzowania porównywania obiektów samemu ? Walki z refleksją, nerw i wszechobecnych hardcodowanych stringów.
Tu macie to na wyciągnięcie nugeta ;)

&nbsp;

 [1]: https://www.nuget.org/packages/NBuilder/