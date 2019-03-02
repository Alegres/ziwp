# System wspomagający zdalne zarządzanie uprawą roślin
## Wprowadzenie
Zamysłem projektu jest stworzenie systemu, umożliwiającego osobom fizycznym kontrolowanie warunków panujących na podlegających im uprawach rolnych, za pomocą intuicyjnego interfejsu graficznego, z poziomu smartphone'a lub aplikacji przeglądarkowej. Dzięki ciągłemu dostępowi do aktualnych danych pomiarowych, osoby zarządające uprawą będą w stanie szybko i efektywnie reagować na zmieniające się parametry, takie jak:
* wilgotność powietrza
* nawodnienie gleby
* temperatura

Gromadzenie pomiarów z uprawy umożliwi stworzenie przydatnych wykresów oraz prognóz, pozwoli również na zautomatyzowanie niektórych czynności (np. uruchomienie zraszaczy, gdy wilgotność gleby spadnie poniżej określonego poziomu). W sytuacji, w której pomiary wskazywać będą na niekorzystny stan uprawy, system generował będzie automatyczne powiadomienia, skierowane do wyznaczonych osób, dzięki czemu będą one mogły podjąć odpowiednie czynności tylko w momencie, w którym jest to faktycznie potrzebne - ograniczony zostanie wysiłek, który w innym wypadku musiałby zostać włożony w manualne dokonywanie pomiarów oraz analizę.

Kluczowym zadaniem systemu będzie więc pomoc w dbaniu o dwa bardzo istotne czynniki
* oszczędność czasu potrzebnego na zarządzanie
* jakość uprawy (jej obfitość, szybki wzrost, zdrowie)

Dzięki temu zaoszczędzone zasoby mogą zostać przeniesione na nowe uprawy, bez konieczności martwienia się o spadek ogólnej jakości.

## Wymagania funkcjonalne
Użytkownik, za pośrednictwem interfejsu graficznego może
* dodawać / usuwać uprawy
* zmieniać nazwę oraz kolor znaczący uprawy (kolor pomoże mu odróżnić wizualnie jedną uprawę od drugiej)
* przeglądać historię zmian kluczowych dla uprawy parametrów (wilgotność powietrza, nawodnienie gleby, temperatura) w czasie
* kontrolować aktualne kluczowe dla uprawy parametry
* ustalać wskaźniki alarmowe dla każdego z parametrów
* ustalać sposób powiadomień na wypadek przekroczenia wskaźników
* odczytać co najmniej jedną prognozę statystyczną opartą na zebranych przez pewien okres czasu danych
* deklarować czynności zautomatyzowane przy pomocy prostej składni bądź formularza (np. uruchamianie zraszaczy w momencie osiągnięcia poziomu X przez parametr A)

Użytkownik otrzyma dostęp do tych możliwości dopiero po *rejestracji* oraz *logowaniu*. Wówczas zostanie stworzona dla niego prywatna przestrzeń robocza, za pośrednictwem której będzie mógł zarządać swoimi uprawami.

Każda nowa uprawa wymagać będzie zainstalowania Arduino oraz *modułu Arduino* w fizycznej lokalizacji uprawy oraz dostosowania go do współpracy z serwerem centralnym
* konfiguracja sieci - przeprowadzana niezależnie
* uruchomienie modułów, konfiguracja (adresy IP, hasła, kluczowe parametry)

## Wymagania niefunkcjonalne
* Bezpieczeństwo systemu - odporność na podstawowe ataki (Sql Injection, XSS), zabezpieczenie komunikacji pomiędzy modułami (SSL), przechowywanie zakodowanych haseł w bazie (SHA-2), testy
* Intuicyjny interfejs - prosta obsługa dla osób nietechnicznych, czytelna czcionka, ograniczenie elementów do minimum, kluczowa funkcjonalność systemu zawsze pod ręką, ograniczenie grafik - skorzystanie z jednoznacznych ikon, responsywny design
* Wysoka dostępność - odporność na awarie, modułowa architektura umożliwia wprowadzenie nadmiarowości (alternatywnych ścieżek na wypadek awarii)
* Skalowalność - system powinien być gotów na łatwą rozbudowę w przyszłości (wykorzystanie wzorców projektowych, framework'ów, zachowanie czystości kodu)
* Aktualna (stale rozwijana) dokumentacja dla użytkowników oraz dokumentacja techniczna
* Ograniczenie danych trafiających do bazy (np. pomiary co określony odstęp czasu), zapewnienie odpowiedniej przestrzeni dyskowej pod dużą ilość danych, gotowość warstwy bazodanowej na duży rozrost
* Poznanie oraz zrozumienie fachowości związanej z realną uprawą roślin

## Ryzyka
* Nieznajomość oraz konieczność uczenia się nowych technologi przez zespół - to co na początku wydaje się łatwe, z czasem może okazać się trudne w implementacji
* Spadek motywacji oraz rozbieżne motywacje wśród członków zespołu
* Czynniki zewnętrzne wpływające na dostępność członków zespołu (choroba, sytuacja rodzinna)
* Niejasne, trudne lub zmieniające się wymagania projektowe oraz brak jasnego harmonogramu (to ryzyko musi zostać zniwelowane już na samym początku!)
* Nieznajomość dokładnej sytuacji rynkowej, zapotrzebowań istniejących wśród osób faktycznych, dbających o istniejące uprawy rolne (ryzyko może zostać zniwelowane dzięki wywiadowi społecznemu)
* Ograniczone zasoby finansowe oraz czasowe możliwe do przeznaczenia na projekt (presja czasu może wpłynąć na jakość kodu, mniejsze pokrycie testami, etc.)

## Architektura systemu
### Podejście ogólne
![alt text](https://github.com/Alegres/ziwp/blob/master/architecture.jpg "Architektura systemu")

### Model z centralnym serwerem

### Model "samowystraczalny"


