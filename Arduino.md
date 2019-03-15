# Szczegóły projektowe - Moduł Arudino
## Założenia
* pobieranie pomiarów z wielu płytek Arduino
* przesyłanie pomiarów do serwera, w celu zapisania ich w bazie danych
* jednoznaczna identyfikacja modułu (uprawy) - w pliku konfiguracyjnym powinien być ustawiany tajny kod, który użytkownik otrzymuje po stworzeniu nowej uprawy
* każda podłączona płytka Arduino również musi być identyfikowana (ponieważ na jednej uprawie może znajdować się wiele grup roślin - w związku z tym system będzie prezentował dla nich inne prognozy oraz ustawiał inne parametry)
* w momencie otrzymania nowego pomiaru z płytki, moduł Arduino musi (na podstawie otrzymanego od serwera wskaźnika) ocenić czy dany parametr, dla danej płytki (części uprawy), nie został przekroczony
* na wypadek przekroczenia wskaźnika, moduł musi powiadomić o tym serwer
