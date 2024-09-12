## Objetivo
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/15/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/15/level2.flag.txt.enc) in the same directory too.
## Solución
```bash
victormcm-picoctf@webshell:~$ ls
level2.flag.txt.enc  level2.py
victormcm-picoctf@webshell:~$ nano level2.py
victormcm-picoctf@webshell:~$ python
Python 3.10.12 (main, Nov 20 2023, 15:14:05) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65)
'39ce'
>>> exit()
victormcm-picoctf@webshell:~$ python level2.py
Please enter correct password for flag: 39ce
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_502ec42e}
victormcm-picoctf@webshell:~$ 
```
## Notas Adicionales

## Referencias
