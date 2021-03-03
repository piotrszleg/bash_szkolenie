# Składnia komend

Wzorzec komendy:

```bash
> <program> <argument-1> <argument-2> ... <argument-n>
```

Cudzysłowy powodują rozpoczęcie czytania argumentu od pierwszego znaku po cudzysłowiu do ostatniego przed cudzysłowiem ignorując znaki specjalne.

```bash
> echo "Hello | World"`
        ^___________^____ jeden argument
< Hello | World
```

Postawienie ukośnika przed cudzysłowiem usuwa jego znaczenie
```bash
> echo "Hello \"World\""
        ^_____________^____ jeden argument
< Hello "world"
```

W przeciwieństwie do większości języków programowania wszystko co wpisujemy w konsolę jest tekstem, nie ma wydzielonego typu string czy function. Dlatego można pisać takie rzeczy:

```bash
"C:/Program Files/Python/python.exe" --version
```

Myślnik (lub dwa myślniki) przed argumentem nie są częścią składnik bash'a, `-o` trafi do programu dokładnie jako `-o`. Dużo programów jednak traktuje argumenty z myślnikami jako klucze a bez myślników jako wartości. 

Popularną konwencją jest też używanie takiego wzorca argumentów:
```bash
> program -i plik_wejsciowy -o plik_wyjsciowy
```

Dużo programów posiada następujące specjalne argumenty:

```bash
> program --version
> program --help
> program --verbose # - tryb "rozgadany" (dalej reszta argumentów) 
```

W unixowych środowiskach (Linux, MacOS i WSL) mamy też do dyspozycji komendę `man <program>` (man jak *manual* - instrukcja obsługi).

# Kierowanie strumieniami

- podłączenie wyjścia jednego programu do wejścia drugiego `|`
- czytanie z/do pliku `>`/`<`
- `2>` redirect stderror
- `command > file 2>&1` redirect stdout i stderror to `file`
- /dev/stdin 
- /dev/stdout

# Ścieżki
- `pwd` komenda na wypisanie obecnego folderu
- `cd <folder>`
- `ls`
- `.` - obecny folder
- `..` - folder wyżej
- ścieżki bez ukośnika lub litery dysku są traktowane jako relatywne
  - plik.txt
  - folder/plik.txt
- ścieżki relatywne explicit (np. do uruchamiania komend w folderze):
  - ./plik.txt
- ścieżki od root'a
  - /bin
  - C:/Users