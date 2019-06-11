Instrukcja obsługi
======================
**PREREKWIZYTY:**
- Serwer, klient WWW oraz moduł Arduino muszą zostać zainstalowane (patrz: dokumentacja poszczególnych modułów)

**KONFIGURACJA PLANTACJI**
1. Stwórz konto za pośrednictwem interfejsu WWW (**Account -> Register**)
    - pamiętaj o użyciu silnego hasła, zawierającego małe oraz duże litery, minimum 9 znaków oraz znaki specjalne
    - wprowadź swoje dane (w tym nazwę użytkownika, email oraz numer telefonu)
    
2. Zaloguj się za pomocą swoich danych.

3. Przejdź do tablicy głównej (**Board**). Aktualnie twoja przestrzeń robocza jest pusta.

4. Stwórz pierwszy Preset (kliknij znak + w menu bocznym)
    - ustaw wszystkie parametry, które będą obowiązywać na twojej plantacji
    
5. Stwórz pierwszą Plantację (kliknij znak + w menu bocznym)
    - ustaw nazwę plantacji oraz wybierz dla niej utworzony preset

6. Po utworzeniu Plantacji wygenerowany zostanie specjalny **tajny kod**. Ten kod będzie potrzebny do skonfigurowania modułu Arduino.

7. Skonfiguruj moduł Arduino.
    - w pliku konfiguracyjnym ustal **tajny kod plantacji**
    - w pliku konfiguracyjnym ustal częstość wysyłania pomiarów
    - w pliku konfiguracyjnym ustal adres IP serwera

8. Podłącz płytkę oraz wszystkie wymagane komponenty do zasilania oraz sieci.

9. Uruchom płytkę
    - od tego momentu możesz śledzić oraz kontrolować aktualną sytuację na swojej Plantacji, za pośrednictwem przeglądarki WWW
