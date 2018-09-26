# ComandiLinuxUbuntu
Principali comandi Linux Ubuntu

#### Numero file in una cartella e sottodirectory
``find . -type f | wc -l``

#### Numero file nella cartella corrente
``ls -l | grep ^- | wc -l``

#### Cerca testo in tutti i file di un certo tipo
``grep -rnw *.php -e 'TEXT'``

#### Tools recuperare spazio
``df -h``  
``ncdu /``  
