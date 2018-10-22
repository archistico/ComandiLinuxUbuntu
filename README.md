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
``rsync -avhp ./demo/ ./demo2``  
z se voglio che comprima 
n oppure --dry-run se voglio vedere prima cosa fa senza fare nulla  
--delete se voglio che cancelli nella destinazione i file in più  
--exclude=nomefile per escludere in remoto un file da non cancellare (tipo configurazione)  
per l'invio su un ssh, mi connnetto e poi:  
``rsync -avhp --delete ./demo/ emilie@ip:~/demo2``  
``rsync -avhp --delete ./demo/ -e "ssh -p 3000" emilie@ip:~/demo2``   
  
#### Raspberry
sudo rpi-update
