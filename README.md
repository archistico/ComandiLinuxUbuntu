# Comandi Linux Ubuntu
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

#### Rimuovi exif metadata dai jpg sia nella cartella che nelle sub
``exiftool -all= -r -overwrite_original -ext jpg .``  

#### Sincronizzazione cartelle
``rsync -av ./demo/ ./demo2``  
