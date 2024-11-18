## Objetivo
The password for the next level is stored in a file called **-** located in the home directory
## Datos De Acceso al Nivel
```
 Servidor: bandit1@bandit.labs.overthewire.org -p 2220
 Contraseña del nivel: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```
## Solución
```bash
bandit1@bandit:~$ pwd
/home/bandit1
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```
## Notas Adicionales

ls - lista los archivos de la carpeta actual
cat - muestra el contenido de varios archivos en la salida estándar

Si elnombre del archivo comienza con - hay que anteponer un /
## Referencias
- [Google Search for “dashed filename”](https://www.google.com/search?q=dashed+filename)
- [Advanced Bash-scripting Guide - Chapter 3 - Special Characters](https://linux.die.net/abs-guide/special-chars.html)