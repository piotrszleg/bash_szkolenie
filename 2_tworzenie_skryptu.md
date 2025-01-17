# Plik ze skryptem

Skrypt powinien zaczynać się od tego typu linijki:

```bash
#!/bin/sh
```

Znak \# to rozpoczyna komentarz, dodatkowe metadane umieszczane w komentarzach to ogólnie częsty zabieg w językach programowania. 

Znak ! w sumie nic nie znaczy, a po nim zapisujemy ścieżkę o interpretera na który pisaliśmy skrypt. Jest już taka umowa że interpretery umieszcza się w folderze `/bin/` tak aby nie było problemu z ich znalezieniem.

Przyjęło się że `/bin/sh` to interpreter jak najbardziej kompatybilny ze standardem Unixa. Oznacza to że skrypt napisany na niego teoretycznie zadziała na każdej dystrybucji Linuxa, iOSie, FreeBSD czy dowolnym programie który zamienia Windowsa w Unixowe środowisko.

Interpreter `/bin/bash` zawiera rozszerzenia GNU. 

Wybór interpretera ma przede wszystkim wpływ składnię, dobrze skonfigurowane interpretery powinny mieć podlinkowane komendy z `/bin/` i `/usr/bin/` ale można też dodawać swoje własne ścieżki czy modyfikować ich zachowanie w plikach konfiguracyjnych. Ogólnie jest straszny chaos i dlatego najlepiej jest używać `/bin/sh` z domyślną konfiguracją, komend z ww folderów i pilnować się aby nasz skrypt był jak najbliższy standardowi Unixa.

Po zapisaniu na naszym skrypcie musimy wykonać komendę:
```bash
chmod +x skrypt.sh
```
(Rozszerzenie pliku nie ma znaczenia na linuxie.)

Dzięki niemu możemy wykonać ten plik o tak:

```
./skrypt.sh
```

Możemy go także podlinkować tak aby był używalny jako komenda w każdym folderze:

```bash
sudo ln -s ./skrypt.sh /usr/bin/skrypt

skrypt
```

Oczywiście uprzedzam że będą problemy z używaniem zmiennej `$0`.

# Argumenty

W naszym skrypcie dostajemy specjalne zmienne:
- `$0` - ścieżka do skryptu
- `$1-$n` - parametry z wiersza poleceń
- `$@` - tablica z parametrami
- `$#` - długość ww tablicy

```bash
#!/bin/sh

echo "Hello $1"
```

Jeżeli chcemy się bawić w takie keyword arguments to znalazłem taki przykład w internecie

[https://www.baeldung.com/linux/use-command-line-arguments-in-bash-script](https://www.baeldung.com/linux/use-command-line-arguments-in-bash-script)

```bash
while getopts u:a:f: flag
do
    case "${flag}" in
        u) username=${OPTARG};;
        a) age=${OPTARG};;
        f) fullname=${OPTARG};;
    esac
done
echo "Username: $username";
echo "Age: $age";
echo "Full Name: $fullname";
```

I możemy go użyć tak:

```bash
./flags.sh -f 'John Smith' -a 25 -u john
```

Nie będę wszystkiego w nim tłumaczył, to taki bardziej snippet do przekopiowania.

Przykład z tej samej strony do używania $@:

```bash
i=1;
for user in "$@" 
do
    echo "Username - $i: $user";
    i=$((i + 1));
done
```

Możemy sobie też tworzyć lokalne komendy za pomocą konstrukcji syntaktycnej function:

```bash

function add(){
    echo $1 "+" $2 | bc
}

add 5 2
```