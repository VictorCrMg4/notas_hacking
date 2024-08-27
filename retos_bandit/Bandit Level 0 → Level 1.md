## Objetivo
The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
## Datos De Acceso al Nivel
```
Servidor: bandit0@bandit.labs.overthewire.org -p 2220
 Contraseña del nivel: bandit0
```

## Solución
```bash
bandit0@bandit:~$ pwd
/home/bandit0
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

bandit0@bandit:~$
```
## Notas Adicionales
```
ls - lista de los archivos en la carpeta actual
pwd - indica el directorio actual
cat - muestra el contenido del archivo que estra como parametro
```
## Referencias