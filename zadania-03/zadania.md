## Zadanie 1

Zaimplementuj algorytm `k-means`. Możesz to zrobić w czystym Pythonie
lub z wykorzystaniem biblioteki `numpy`. Początkowy wybór centroidów
ma być losowy z (dyskretnym) rozkładem jednostajnym. Zaprezentuj
obliczone klastry w formie graficznej (`matplotlib` z wykresem typu
`scatter`, każdy klaster innego koloru).

## Zadanie 2

Dla algorytmu z zadania 1 zmień sposób wybierania początkowych
centroidów. Pierwszy wybierz losowo, a każdy następny wybierz z
jeszcze niewybranych punktów z prawdopodobieństwem proporcjonalnym do
kwadratu odległości między tym punktem a najbliższym centroidem.
