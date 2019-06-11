Wnioski projektowe
====================
# Podsumowanie
Dzięki jasno wyznaczonemu zakresowi pracy oraz kompleksowemu projektowi, udało się zrealizować postawione cele. Powstał w pełni działający system, w którym użytkownik może:

* Założyć konto (tworząc jednocześnie prywatną przestrzeń roboczą)
* Zalogować się na swoje konto
* Dodawać plantacje, usuwać je, zarządzać nimi, przeglądać ostatnie pomiary oraz wykresy
* Dodawać presety oraz zarządzać nimi
* Zmieniać ustawienia swojego konta

Aplikacja prezentuje się prawidłowo oraz działa tak samo wydajnie zarówno w przeglądarkach internetowych na komputery stacjonarne, jak i urządzenia mobilne.

Dzięki frameworkowi *Vue.js*, praca z systemem jest dynamiczna. Udało się skondensować wiele elementów w pojedynczych widokach, bez utraty czytelności, ze względu na wprowadzenie okien modalnych, rozwijanych list, czy zakładek, których treść generowana jest dynamicznie, bez potrzeby odświeżania strony.

Aplikacja wciąż wymaga dopracowania w kilku kwestiach. Przede wszystkim komunikacja *użytkownik - klient* powinna odbywać się za pośrednictwem *protokołu SSL*, w celu uniemożliwienia przechwycenia niezaszyfrowanych pakietów przez osoby trzecie. Wykradnięcie chociażby przechowywanego w nagłówkach żądań HTTP *tokenu JWT*, którego klient używa do autoryzacji przed serwerem, spowodowałoby, że nieproszona osoba mogłaby nielegalnie podszyć się pod użytkownika, którym faktycznie nie jest. Należy zwrócić również uwagę na politykę bezpieczeństwa *tokenów JWT*, min. dobór algorytmów szyfrujących, czy długości życia tokenu. Projektem, wdrożeniem oraz ciągłym dbaniem o mechanizmy bezpieczeństwa, powinny zająć się wysoko wyspecjalizowane osoby, mające dużą wiedzę na temat możliwych ataków, przeprowadzanych we współczesnym świecie.

**UWAGA:** Komunikacja Klient-Serwer została zabezpieczona za pomocą protokołu *SSL*.

System powinien zostać poddany intensywnym testom, w celu upewnienia się, że przed udostępnieniem go szerszemu gronu odbiorców, działa na pewno tak, jak powinien. Wskazane jest również dokonanie kolejnej analizy funkcjonowania systemu, w celu ustalenia co jeszcze można w nim poprawić. Szereg usprawnień może zostać wprowadzony przede wszystkim w interfejsie użytkownika. Pomocne przy ocenie efektywności aplikacji z pewnością okaże się zdanie grupy zwykłych użytkowników, którym system powinien zostać udostępniony do przetestowania, jeszcze przed oficjalnym opublikowaniem.

Skorzystanie ze współcześnie popularnych oraz dynamicznie rozwijających się technologii, z pewnością znacznie ułatwiło pracę nad aplikacją. Technologie te narzucają pewne standardy w pisaniu kodu oraz strukturyzowaniu projektu, dzięki czemu automatycznie staje się on czytelniejszy dla innych programistów oraz łatwiejszy w rozwijaniu. W celu rozszerzenia grupy programistów, pracujących nad systemem, wskazane byłoby jednak jeszcze dokładniejsze udokumentowanie kodu aplikacji (w tym również stworzenie developerskiej dokumentacji).

W przypadku dalszych prac nad systemem, skonfigurowane powinno zostać narzędzie typu *Continous Integration* oraz napisane powinny zostać odpowiednie testy jednostkowe i integracyjne, w celu umożliwienia wczesnego, zautomatyzowanego wykrywania ewentualnych błędów związanych ze zmianami w kodzie, przed wypuszczeniem produkcyjnej wersji aplikacji.

Wciąż istotna pozostaje kwestia opracowania strategii na udostępnienie systemu do użytku publicznego. Aplikacja może działać jako jedyna centrala, do której dostęp mają wszyscy, niezależni użytkownicy z całego świata, lub być udostępniana na licencji umożliwiającej wdrożenie jej w strukturach konkretnych organizacji, firm, szkół, etc.

Stopniowo, w ramach wprowadzania udoskonaleń oraz przy ciągłej analizie rynku oraz zdania użytkowników testujących oraz korzystających z aplikacji, wprowadzane powinny być bardziej zaawansowana, a nawet innowacyjne mechanizmy. Przykładem takiej innowacji mogłoby być zaimplementowanie sztucznej inteligencji, która wnikliwie analizowałaby sytuację na plantacjach użytkowników, wyłapywała pewne schematy, a następnie pomagała użytkownikowi jeszcze lepiej zarządzać plantacjami.

Ciekawą opcją wydaje się również połączenie systemu z różnymi zewnętrznymi *API*, na przykład *Google Maps*. Konkretne plantacje mogłyby wówczas zostać związane z lokalizacjami.

Wskazane byłoby również opracowanie wersji aplikacji, działającej na systemach *Android* oraz *iOS*, jako samodzielny program, uruchamiany poprzez plik wykonywalny, a nie przeglądarkę internetową.

Wprowadzanie takich dodatkowych funkcjonalności wymaga jednak rozszerzenia zespołu pracującego nad aplikacją, dalszej kompleksowej fazy projektowej oraz, z pewnością, nakładów finansowych, dlatego na ten moment są to jedynie rozważania hipotetyczne.

Aktualnie aplikację można traktować jako solidną bazę, nadającą się do dalszego rozwoju.

# Ostateczny kosztorys
Ostatecznie poniesione zostały następujące koszta:
```
5$ + 285,5zł =~ 300 zł
```

* Opłacenie publicznego serwera testowego, dzięki któremu mogliśmy testować współdziałanie wszystkich modułów: **5$**

**Arduino:**

* Arduino UNO	92 zł
* Powłoka Ethernet	47 zł
* DHT22	30 zł
* czujnik wilgotności gleby	6 zł
* przekaźnik	8 zł
* zasilacz	25 zł
* pompa	40 zł
* switch	12,5 zł
* przewód sieciowy	15 zł
* drobna elektronika	10 zł


