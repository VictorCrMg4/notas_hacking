## Objetivo
The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.
## Datos De Acceso al Nivel
```
Servidor: bandit4@bandit.labs.overthewire.org -p 2220
Contraseña del nivel: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```
## Solución
```bash
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$
bandit4@bandit:~/inhere$ ls
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09
bandit4@bandit:~/inhere$ man file
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./file07
cat: ./file07: No such file or directory
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
bandit4@bandit:~/inhere$
```
## Notas Adicionales
cat * - muestra todos los archivos del directorio actual
## Referencias