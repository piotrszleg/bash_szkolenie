# Porady końcowe

Nie bójcie się kopiować całych programów z intenetu lub na części. Wszyscy tak robią.

Lepiej coś sprawdzić używając `man` lub na https://man7.org niż ufać randomowi ze stack overflow.

Wzystko możecie zrobić na 1000 sposobów, są setki implementacji interpretera czy programów z user space, raczej rzadko ktoś myśli nad tym jaka metoda jest najlepsza.

Jeżeli chodzi o wydajność, to jeżeli możecie coś zrobić jednym programem to tak będzie szybciej, bo programy z user space są zazwyczaj szybsze od skryptów w bash'u.

Bash może i często jest szybszy od Pythona jeżeli używacie komend i przekierowywania strumieni a nie jego rzeczywistej składni czyli na przykład pętli i ifów.

Skrypty w bashu są ogólnie mało czytelne, warto pokusić się o zmienne czy komentarze.

Uważajcie na komendę `rm` (: