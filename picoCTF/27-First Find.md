## Objetivo
Unzip this archive and find the file named 'uber-secret.txt'
## Solución
```bash
victormcm-picoctf@webshell:~$ ls
files  files.zip
victormcm-picoctf@webshell:~$ strings files.zip | grep pico
picoCTF{f1nd_15_f457_ab443fd1}
```
## Solución 2
```bash
victormcm-picoctf@webshell:~$ ls
files  files.zip
victormcm-picoctf@webshell:~$ find ~/ -name "uber-secret.txt"
/home/victormcm-picoctf/files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
victormcm-picoctf@webshell:~$ cd files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/
victormcm-picoctf@webshell:~/files/adequate_books/more_books/.secre
t/deeper_secrets/deepest_secrets$ ls
uber-secret.txt
victormcm-picoctf@webshell:~/files/adequate_books/more_books/.secre
t/deeper_secrets/deepest_secrets$ cat uber-secret.txt 
picoCTF{f1nd_15_f457_ab443fd1}
```
## Notas Adicionales
find sirve para buscar archivos
## Referencias