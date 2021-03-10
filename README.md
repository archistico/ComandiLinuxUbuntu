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
raspivid -o - -t 0 -vf -hf -fps 30 -b 6000000 | ffmpeg -re -ar 44100 -ac 2 -acodec pcm_s16le -f s16le -ac 2 -i /dev/zero -f h264 -i - -vcodec copy -acodec aac -ab 128k -g 50 -strict experimental -f flv rtmp://a.rtmp.youtube.com/live2/[Codice seg]
  
#### Salva output in file ( >> append )
ls > output
ls >> output

#### GIT
git init  
git add .  
git commit -m'...'  
git push origin master  
git pull origin master  
git config credential.helper 'store'  

##### resettare le modifiche locali
```
git reset --hard
git pull origin master
```

##### windows cartelle case-sensitive
fsutil.exe file setCaseSensitiveInfo "C:\my folder" enable
deve essere fatto su tutti i subfolder

#### Vagrant
vagrant box add laravel/homestead  
cd ~  
git clone https://github.com/laravel/homestead.git Homestead  
cd Homestead  
bash init.sh  
ssh-keygen -t rsa -C “your_email@example.com”  
```
authorize: c:/Users/USER_NAME/.ssh/id_rsa.pubkeys:  
— c:/Users/USER_NAME/.ssh/id_rsa  
```
vagrant box update  
vagrant box remove laravel/homestead --box-version=7.2.1   
  
.bash-profile
```  
# Some shortcuts for easier navigation & access  
alias ..="cd .."  
alias vm="ssh vagrant@127.0.0.1 -p 2222"  
  
# Homestead shortcut  
function homestead() {  
    ( cd ~/Homestead && vagrant $* )  
}    
```  
#### Cancellare file con caratteri strani
`ls -ali`  
`sudo find . -inum <numero> -exec rm -i {} \;`  


## CREAZIONE UBUNTU SERVER IN VIRTUALBOX
sudo rm -rf /var/www  
sudo ln -s /home/emilie/condivisa /var/www  
sudo usermod -a -G vboxsf www-data  
  
Riavviare la macchina  
  
impostazioni virtualbox  
  
in file->gestione reti host  
192.168.2.100 e no DHCP  
(l'indirizzo della macchina avrà un numero in più)  

scheda 1 NAT  
scheda 2 Scheda solo host   
  
file: /etc/netplan/emilie.yaml  
network:  
    version: 2  
    renderer: networkd  
    ethernets:  
        enp0s3:  
            dhcp4: true  
        enp0s8:  
            dhcp4: no  
            dhcp6: no  
            addresses: [192.168.2.101/24]  
            nameservers:   
                 addresses: [8.8.8.8, 8.8.4.4]  
                 
  
sudo netplan generate  
sudo netplan apply  

# ALIAS
```  
alias todo='python /c/Script/todo.py'
alias gadd='git add .'
alias gpush='git push origin master'
alias gstatus='git status'
alias gfetch='git fetch --all'
alias greset='git reset --hard origin/master'
alias reloadbash='source ~/.bashrc'
alias phpserver='php -S 127.0.0.1:8000'
alias cd..='cd ..'
alias git-bash='/git-bash.exe & > /dev/null 2&>1'
```  

# Youtube-dl
```  
youtube-dl.exe -x --audio-format mp3 -c -w -i PLR73VO6XmiXX8yzysPuY1ssEBMcR5k2hT
./youtube-dl.exe --ffmpeg-location "ffmpeg/bin" -x --audio-format mp3 -c -w -i PLR73VO6XmiXWM8h_9tLIZOSLEMpkjGoZs
```  

# LINUX 
file per IP statico dato da impostazione MAC address da router  
/etc/network/interfaces

```  
auto lo
iface lo inet loopback
iface eth0 inet manual
```  
