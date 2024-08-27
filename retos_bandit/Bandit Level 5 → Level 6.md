## Objetivo
The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

## Datos De Acceso al Nivel
```
Servidor: bandit5@bandit.labs.overthewire.org -p 2220
Constraseña del nivel: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```
## Solución
```bash
bandit5@bandit:~/inhere$ ls -R
.:
maybehere00  maybehere04  maybehere08  maybehere12  maybehere16
maybehere01  maybehere05  maybehere09  maybehere13  maybehere17
maybehere02  maybehere06  maybehere10  maybehere14  maybehere18
maybehere03  maybehere07  maybehere11  maybehere15  maybehere19

./maybehere00:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere01:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere02:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere03:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere04:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere05:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere06:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere07:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere08:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere09:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere10:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere11:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere12:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere13:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere14:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere15:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere16:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere17:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere18:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere19:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3
bandit5@bandit:~/inhere$ find . -type f -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

```
## Notas Adicionales
ls -R lista los archivo de manera recursiva
find . -type f -size 1033c - busca un  archivo de tipo regular  y de tamaño de 1033 bytes

## Referencias