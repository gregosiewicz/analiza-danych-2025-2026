## Zadanie 1

Przygotuj dwa obiekty `GeoDataFrame`: `wojewodztwa` i `miasta`.

Wymagane pola:

- `wojewodztwa`
  - `id`
  - `nazwa`
  - `geometria`
- `miasta`
  - `id`
  - `nazwa`
  - `ludnosc`
  - `geometria`

1. Ze strony
   [gisco-services.ec.europa.eu](https://gisco-services.ec.europa.eu/distribution/v2/nuts/download/)
   pobierz dane w skali 1:10 milionów w formacie `GeoJSON` z 2024
   roku. Znajdź plik `NUTS_RG` z układem współrzędnych `4326` i poziomem
   agregacji `LEVL_2`. Wczytaj dane do `GeoDataFrame`, wybierz polskie
   województwa (`CNTR_CODE == "PL"`), zostaw potrzebne kolumny i zapisz
   te dane w pliku `wojewodztwa.geojson`.
2. Pobierz dane o punktach środkowych polskich miast z OpenStreetMap.
   Wykorzystaj [Overpass Turbo](https://overpass-turbo.eu),
   uruchamiając zapytanie:

   ```text
   [out:json];

   {{geocodeArea:Poland}}->.pl;

   (
     nwr["place"~"^(city|town)$"](area.pl);
   );

   out center tags;
   ```

   Następnie wyeksportuj wynik do `GeoJSON`, wczytaj go do
   `GeoDataFrame` `miasta` i zachowaj co najmniej nazwę, liczbę
   ludności oraz geometrię.
3. Wykonaj następujące analizy przestrzenne:
   1. Podaj liczbę miast leżących w poszczególnych województwach.
   2. Posortuj województwa względem liczby miast.
   3. Podaj liczbę mieszkańców miast w poszczególnych województwach.
   4. Posortuj województwa względem gęstości zaludnienia, liczonej jako
      liczba mieszkańców miast na kilometr kwadratowy powierzchni
      województwa.
   5. Podaj liczbę miast, które są oddalone od Warszawy o co najwyżej
      50 km.
   6. Znajdź miasto, dla którego suma odległości od wszystkich innych
      miast jest najmniejsza.

## Zadanie 2

Ze strony [dane.gov.pl](https://dane.gov.pl) pobierz dane o położeniu
nadajników 5G dla częstotliwości 3600 MHz. Wczytaj je do `GeoDataFrame`
i wykonaj analizę pokrycia.

1. Przygotuj geometrię punktową nadajników i przekształć dane do
   `EPSG:2180`.
2. Dla każdego nadajnika utwórz bufor (pokrycie) o promieniu 1 km.
3. Oblicz dla każdego województwa powierzchnię pokrytą sygnałem 5G i
   wypisz województwa posortowane według poziomu pokrycia.
4. Dla każdego województwa przygotuj ranking operatorów według
   wielkości pokrycia. Zadbaj o to, aby nakładające się bufory tego
   samego operatora nie zawyżały wyniku.
