# Szczegóły projektowe - klient
## Założenia
* prosty oraz intuicyjny interfejs
* dynamiczne odświeżanie elementów strony (bez konieczności ręcznego odświeżania - *Ajax*)
* czytelne czcionki, brak elementów rozpraszających użytkownika
* wykorzystanie prostych ikon, ułatwiających odnalezienie konkretnych elementów na stronie
* ograniczenie ilości zapytań kierowanych do serwera
* dobre ustrukturozywanie kodu (zachowanie zasad *Clean Code*, zapewnienie łatwej rozszerzalności)
* łatwy dostęp do wszystkich elementów interfejsu (głębokość na maksymalnie trzy kliknięcia)
* spójne formatowanie kodu (zapewnione dzięki IDE - *Visual Code*)
* podział elementów składowych systemu na małe komponenty (zarządzanie mniejszymi fragmentami jest o wiele łatwiejsze)
* (możliwa obsługa wielu języków)

## Podstawowe rozwiązania
### Vue.js
Wybrany został framework *Vue.js* pozwalający tworzyć dynamiczne strony WWW przy wykorzystaniu *javascript*. Vue jest bardzo dobrze udokumentowany oraz zawiera szereg pomocnych bibliotek. Pozwala w bardzo prosty sposób podzielić widok na mniejsze komponenty, które następnie mogą być używane w wielu miejscach systemu. Ponadto praca nad mniejszymi fragmentami zawsze jest prostsza.

### Axios
Axios pozwala w bardzo prosty sposób tworzyć zapytania do API (serwera)
```
const axios = require('axios');

// Make a request for a user with a given ID
axios.get('/user?ID=12345')
  .then(function (response) {
    // handle success
    console.log(response);
  })
  .catch(function (error) {
    // handle error
    console.log(error);
  })
  .then(function () {
    // always executed
  });
```

W celu umożliwienia łatwej zmiany biblioteki, stworzone zostaną specjalne *service*, wykorzystywane przez klienta do komunikacji z serwerem. Dzięki temu ewentualna zmiana biblioteki służącej do komunikacji z serwerem będzie łatwa - wystarczy wprowadzić nową implementację serwisu.

### Vuex
*Vuex* jest rozszerzeniem *Vue.js*, funkcjonującym jako centralny magazyn gromadzący dane, z których następnie (w kontrolowany sposób) mogą korzystać wszystkie komponenty widoku.

![alt text](https://raw.githubusercontent.com/vuejs/vuex/dev/docs/.vuepress/public/vuex.png "Vuex")

Jest to bardzo przydatne rozszerzenie, zwłaszcza biorąc pod uwagę to, że klient pobierał będzie od serwera dane, wykorzystywane następnie w wielu miejscach. Klient będzie również zmieniał te dane. W związku z tym nie tylko serwer będzie musiał zostać powiadomiony o zmianie, ale i każdy komponent widoku. Dzięki Vuex utrzymanie spójności jest bardzo proste.


### i18n
Rozszerzenie umożliwiające wprowadzenie wielu wersji językowych.

### Bootstrap
*Bootstrap* jest frameworkiem, który pozwala na tworzenie eleganckich, responsywnych widoków, przy użyciu *HTML oraz CSS*. Posiada szereg zdefiniowanych klas, dzięki czemu tworzenie widoku jest szybkie.

### Autoryzacja przy pomocy tokena JWT
Jako że w komunikacji *klient-serwer* stawiamy na podejście *REST*, **token JWT** będzie idealnie pasował do naszego systemu. Klient, w momencie logowania, otrzyma od serwera specjalny token, w którym zakodowana jest tożsamość logującego się użytkownika. Serwer, dzięki mechanizmom wewnętrznym, potrafi ocenić prawdziwość tokena oraz pobrać z niego obiekt użytkownika, który się nim posługuje. Dzięki temu zabezpieczone zostaną zasoby, do których dostęp powinien mieć tylko zalogowany użytkownik oraz zwrócone zostaną tylko i wyłącznie zasoby należącego do konkretnego użytkownika.

## Struktura implementacji
![alt text](https://github.com/Alegres/ziwp/blob/master/client_structure.png?raw=true "Client structure")

* assets - statyczne pliki *.js*, *.css* oraz obrazki
* components - komponenty budujące stronę (np. wyszukiwarka, przełącznik wersji językowej)
* constants - pliki zawierające zmienne stałe (pliki konfiguracyjne)
* lang - pliki z wersjami językowymi
* pages - konkretne fragmenty systemu (komponenty) posiadające kluczową biznesową rolę
* plugins - pliki stanowiące interfejs do wykorzystywanych w systemie pluginów (*Toast* - elegancka obsługa błędów, *i18n* - wsparcie dla wielu wersji językowych, etc.)
* router - pliki odpowiedzialne za obsługę *routingu* w systemie (gdzie skierować użytkownika, gdy wejdzie pod dany adres)
* services - serwisy wykorzystywane przez system do komunikacji z serwerem oraz do innych zadań (weryfikacja adresu email, hasła, etc.)
* store - pliki definiujące magazyn *Vuex*

## Projekt interfejsu
Poniżej przedstawiony został projekt interfejsu (wraz z zaznaczonymi komponentami odpowiedzialnymi za daną część).

![alt text](https://github.com/Alegres/ziwp/blob/master/interface_1.jpg?raw=true "Interface 1")

* #APP - główny komponent, *wrapper* dla całej aplikacji
* #NAVBAR - górne menu, zawiera informacje o aktualnie zalogowanym użytkowniku oraz akcje związane stricte z jego kontem (wyloguj się, przejdź do ustawień); wykorzystanie dwóch ikon (**mini_user.ico** oraz **settings.ico**)
* #SIDEBAR - menu boczne, może być rozwijane (**toggle on / off**), dzięki czemu w wersji mobilnej użytkownik będzie miał wciąż dużą ilość miejsca na środku ekranu. Zawiera odnośniki do najważniejszych (pod względem realizacji założeń biznesowych) elementów systemu: zakładanie uprawy, tworzenie presetów, zarządzanie uprawami.
* #MAINBAR - w ten komponent wstrzykiwane będą kolejne komponenty, odpowiedzialne za realizację kluczowej funkcjonalności systemu (formularze służące do dodawania presetów / upraw, szczegóły konkretnej uprawy, panel zarządzania uprawą, etc.)

## Dodawanie uprawy
Za pomocą formularza zawartego w komponencie **#CREATE_PLANT** użytkownik będzie mógł dodać do systemu uprawę. W momencie wysłania formularza, do serwera zostanie skierowane zapytanie *POST*, zawierające dane dotyczące nowej uprawy (preset oraz nazwę). Serwer spróbuje stworzyć nową uprawę i zwróci odpowiednią informację do klienta (błąd lub wygenerowany kod uprawy).

![alt text](https://github.com/Alegres/ziwp/blob/master/create_plant.jpg?raw=true "Create plant")

Patrząc głębiej w działanie klienta:
* state - nic innego, jak faktyczne dane (tablice, stringi, inty)
* mutations - za pomocą *mutacji* zmieniamy stany (dzięki temu dostęp do stanów jest kontrolowany). Wszystkie zmiany stanów **muszą** przechodzić przez mutacje
* actions - są asynchroniczne, wyzwalają mutacje (*commitują* je). Wewnątrz akcji możemy np. wysyłać zapytania do serwera - w naszym przypadku korzystając z odpowiednich serwisów.

**Przykład:**
```
    login({ dispatch, commit }, { username, password }) {
        commit('loginRequest', { username });
    
        UserService.login(username, password)
            .then(
                user => {
                    commit('loginSuccess', user);
                    router.push('/');
                },
                error => {
                    commit('loginFailure', error);
                    dispatch('alert/error', UserMessagesService.getMessageAfterLogin(error.response), { root: true });
                }
            );
    }
```
Akcja *login* jako argument przyjmuje *username* oraz *password*. Na początku wykonuje ona *commit*, wywołujący mutację:
```
    loginRequest(state, user) {
        state.status = { loggingIn: true };
        state.user = user;
    }
```
Powyższa mutacja zmienia *state* ustawiając użytkownika na tego, który próbuje się zalogować oraz parametr *loggingIn* na *true* (dzięki temu wiemy, że aktualnie loguje się jakiś użytkownik).

Przepływ jest więc następujący:
* AKCJA -> MUTACJA -> ZMIANA STANU

![alt text](https://github.com/Alegres/ziwp/blob/master/vuex.jpg?raw=true "Vuex")

## Dodawanie presetu

## Zarządzanie uprawą

## Ustawienia konta
