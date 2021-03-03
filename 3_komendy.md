- `man <program>` - otwiera dokumentację programu w konsoli
- echo - wypisz argumenty
- cat - wypisz plik 
- less - wypisz plik ale stopniowo (spacja - przewijanie w dół, q - wyjście)
- xargs - wywołuj program z kolejnymi pobranymi linijkami

```bash
echo "1\n2\n3" | xargs -n 1 echo "-"

echo "1\n2\n3" | xargs -I {} -n 1 echo {},

touch test.log
mkdir logs
# wszystkie pliki .log przerzucamy do folderu logs
find . -name "*.log" | xargs -I {} -n 1 mv {} logs/{}
rm -r logs
```
- `sh -c` - odrobinę ułatwia korzystanie z xargs
```bash
echo "1\n2\n3" | xargs -n 1 sh -c 'echo "<$0>"'
```
- bc - kalkulator
```bash
echo "2+2" | bc
```
- awk 

```bash
# Usuwamy cale zakomentowane linie z programu:
program="# komentarz\na=1\n# drugi komentarz\nprint(a)"
echo -e $program | awk "/^[^#]/"
```

- read

```
echo "username:"
read username
echo "hello $username"
```