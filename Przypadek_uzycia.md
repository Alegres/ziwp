# Ogólny przypadek użycia

## 1. Użytkownik zakłada konto za pośrednictwem klienta WWW
![alt text](https://github.com/Alegres/ziwp/blob/master/registration_ziwg.jpg?raw=true "Registration")

**Przykładowy model użytkownika:**
```
{
  "useremail": "test@test.pl",
  "salt": "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08",
  "hash": "4417a30dc8c6b53f5e2e2b9051159348036017f9061e8ace1f966a1ab58fbedd"
}
```

## 2. Użytkownik loguje się do systemu
W momencie wysłania formularza, klient kieruje do serwera zapytanie *POST*, zawierające dane użytkownika - adres mailowy oraz hasło. Serwer kontaktuje się z bazą danych, w celu zweryfikowania danych. Jeśli są one prawidłowe, generuje **token JWT**, który następnie zwraca do klienta. Od tej pory klient może potwierdzać swoją tożsamość przed serwerem. Token musi być dostarczony jako nagłówek każdego requestu płynącego od klienta do serwera, proszącego o zasoby, które powinny być zabezpieczone. Na podstawie tokenu, serwer będzie również w stanie rozpoznać jaki użytkownik się nim posługuje (w tokenie zakodowany jest posługujący się nim użytkownik). Dzięki temu zawsze zwróci zasoby, które należą do konkretnego użytkownika.
![alt text](https://github.com/Alegres/ziwp/blob/master/login_ziwg.jpg?raw=true "Login")

Klient zapisuje token w swojej pamięci lokalnej, dzięki temu jest w stanie posługiwać się nim zawsze, gdy zajdzie taka potrzeba.

![alt text](https://github.com/Alegres/ziwp/blob/master/save_token_ziwg.jpg?raw=true "Save token")

## 3. Przestrzeń robocza użytkownika
Przestrzeń użytkownika jest bardzo prosta. Składa się na nią kilka mniejszych komponentów:
* #NAVBAR - zawiera przycisk pozwalający na wylogowanie oraz przejście do ustawień użytkownika
* #SIDEBAR - zawiera główne akcje, które może wykonać użytkownik (*Create a plan*) oraz aktualne uprawy użytkownika.
* #MAIN - główna część przestrzeni roboczej

![alt text](https://github.com/Alegres/ziwp/blob/master/main_workspace_ziwg.jpg?raw=true "Workspace")

## 4. Użytkownik tworzy plantację
Za pośrednictwem formularza, użytkownik może stworzyć nową plantację oraz przypisać do niej preset.

![alt text](https://github.com/Alegres/ziwp/blob/master/create_plant_ziwg.jpg?raw=true "Create a plant")

**Przykładowy preset:**
```
{
  "name": "Canabis",
  "goodTemperature": 23,
  "goodHumidity": 70,
  "waterPerDay": 1,
  "howManyTimesToWater": 3,
  "expectedGrowth": 2
}
```

Preset zawiera podstawowe parametry dla konkretnej uprawy. Posłużą one do stworzenia prognozy wzrostu rośliny oraz kontroli parametrów panujących na uprawie.

Użytkownik otrzymuje również od serwera tajny kod plantacji, dzięki któremu będzie mógł skonfigurować swój moduł Arduino.
