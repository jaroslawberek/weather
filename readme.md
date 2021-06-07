# Weather
Weather jest aplikacją napisaną w celu rekrutacji na stanowisko programisty. Specyfikacja aplikacji została wysłane w emailu i wg niej oraz rozmowy telefonicznej, został utworzony projekt.

##Specyfikacja
Korzystając z publicznie dostępnych usług sieciowych, stwórz aplikację, która będzie pobierała i wyświetlała w dowolnym miejscu strony informację na temat pogody w wybranym przez użytkownika mieście.
Aplikacja powinna umożliwiać:
Sprawdzenie przez każdego użytkownika stanu aktualnej pogody w wybranym z przedefiniowanej listy mieście. W wypadku braku połączenia z zewnętrznymi usługami, wyświetlony powinien być ostatni stan pogody. Aplikacja powinna umożliwiać odświeżenie informacji pogodowych bez przeładowania strony.
Dla ograniczonej grupy użytkowników aplikacja powinna umożliwiać:
Konfigurację adresu usługi sieciowej wykorzystywanej do pobierania danych pogodowych (np. yahoo).
Edycję listy miast (dodawanie, usuwanie, zmiana) dla których możliwe jest sprawdzenie pogody

Zalecane jest, aby rozwiązanie umożliwiało rozszerzenie swojej funkcjonalności również na innych dostawców danych pogodowych.
Należy użyć framework'a Symfony, działającego na Docker z PHP Możliwość użycia bibliotek firm trzecich.

##Technologia

Projekt stworzono w oparciu o Laravel 5.8 (w rozmowie telefonicznej zezwolono na ten framework), MySql dbMaria, jQuery, boostrap4
Projekt testowany był na xampp ver. 3.2.4

## Installation

Po pobraniu projektu z repozytorium należy w konsoli uruchomić (po przejsciu do projektu)


```
npm install
```
oraz

```
composer update
```

Nastepnie aby w bazie pojawiły sie tabele ze wstępnymi rekordami należy uruchomić migracje wraz z opcja --seed

```
php artisan migrate:fresh --seed
```
Wcześnij należy oczywiści utorzyć baze danych w srodowisku MySql. Aplikacja zakłada nazwe bazy: weather, użytkownika: root bez podania hasla. W razie konieczności dane logowania trzeba poprawić w pliku .env znajdującego w katalogu głowownym aplikacji.

##Wykonanie

Do określenia aktualnej pogody użyłem https://openweathermap.org/api. W pliku config/weather znajdują się podstawowe ustawienia takie jak token oraz co jaki czas trona w AJAX ma pobierać stan pogody.

Aplikacja zbudowana jest w oparciu o MVC oraz wykozystanie wzorców projektowych takich jak Gateway oraz Repozytory (katalog App/Weather).
Obiekt OpenWeatherCurrentWeatherRepository, który implementuje interface  CurrentWeatherRepositoryInterface za pomocą cUrl pobiera informacje o pogodzie a nastepnie zwraca obiekt typu CurrentWeater. Aby dodać innego dostawce informscji o aktualnej pogodzie nalezy utworzyć nowy obiekt implementujący interface CurrentWeatherRepositoryInterface w configuracji ustawić token i inne istotne dane, a nastpnie w plku App/Providers/AppServiceProvider dokonać przełączenia wskazania interfajsu na odpowedni obiekt resposytory.

Po zalogowaniu sie istaniej możliwość dodawania usuwania  miasta oraz wskazania, które miasto ma być domyślnie ustawione.

Dane pogodowe są oczywiści w okrojonej formie - nie było założeń jakie informacje dokładnie być przedswione dlatego pokazuje te najważniejsze wg mnie.

## License

## Author

Jarosław Berek
