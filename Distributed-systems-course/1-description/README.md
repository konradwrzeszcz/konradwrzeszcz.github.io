## Co to jest system rozproszony (distributed system)?
*   system działający na wielu maszynach połączonych siecią
*   charakteryzują go 
    * awarie częściowe (partial failures)
        *   awaria częściowa - w systemie rozproszonym, część systemu może nie działać, gdy z pozostałą częścią wszystko jest w porządku
        *   z punktu widzenia oprogramowania, nie jest możliwe zdobyć informacji o tym dlaczego inna część systemu nie działa, bez pomocy globalnego narzędzia monitorującego
        *   prawdopodobieństwo awarii jest duże
    * nieograniczone opóźnienie sieci (unbounded latency) - sieć może zachowywać się w nieprzewidywalny sposób

## Awaria częściowa
### Pytanie (query) - Możliwe problemy z przesłaniem zapytania między maszynami M1 i M2

![alt_text](images/query.png "image_tooltip")


1. Request z M1 do M2 zaginie (np. przez problemy z siecią)
2. Przesłanie zapytania z M1 do M2 może być za wolne dla M1

![alt_text](images/request_too_slow.png "image_tooltip")


3. M2 może być wyłączona

![alt_text](images/machine_crashed.png "image_tooltip")


4. Przetwarzanie zapytania przez M2 trwa za długo

![alt_text](images/slow_processing.png "image_tooltip")


5. Przesyłanie odpowiedzi z M2 do M1 może być za wolne dla M1

![alt_text](images/response_too_slow.png "image_tooltip")


6. Odpowiedź z M2 do M1 może zaginąć

![alt_text](images/response_lost.png "image_tooltip")

**Z perspektywy M1, żadna z podanych sytuacji nie jest rozróżnialna. Nie jest możliwe uzyskanie informacji dlaczego odpowiedź nie przyszła.**


7. Innym rodzajem problemów może być problem [bizantyjskich generałów](https://en.wikipedia.org/wiki/Byzantine_fault), gdzie M2 nadal działa, ale zwraca błędne informacje.



### Żądanie (command)

![alt_text](images/command.png "image_tooltip")


**Nie można założyć, że jeżeli M1 nie dostanie odpowiedzi “OK”, wartość X to nadal 5.
</br>
Błąd niekoniecznie musiał wystąpić przed zmianą wartości X.**



## Nieograniczone opóźnienie (unbounded latency)

Opóźnienie na sieci jest nieprzewidywalne.

### Jak ustawić <em>timeout</em> dla systemu rozproszonego dla zapytania?

![alt_text](images/how_to_set_timeout.png "image_tooltip")


```
Timeout = 2d + r
d - maksymalna wartość opóźnienia na sieci 
r - maksymalny czas przetwarzania zapytania
```

**Nie jest to jednak prawdziwe, dla wszystkich przypadków w systemach rozproszonych przez nieograniczone opóźnienie sieci.**



## Po co budować system rozproszony?
- Brak możliwości przetworzenia/zapisania danych na pojedynczej maszynie (np. Google posiada za dużo danych dla pojedynczej maszyny)
- Przyspieszenie systemu
- Skalowalność - możliwość zwiększenia ilości instancji aplikacji do przetworzenia większej ilości danych (np. przy zwiększonej aktywności użytkowników)
- [Redundancja](https://en.wikipedia.org/wiki/Redundancy_(engineering)) - duplikacja krytycznych części systemu, by zwiększyć niezawodność systemu (np. backupy danych)