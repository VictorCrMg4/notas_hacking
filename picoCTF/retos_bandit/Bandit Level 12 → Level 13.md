## Objetivo
The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)
## Datos De Acceso al Nivel
```
Servidor: bandit12@bandit.labs.overthewire.org -p 2220
Contraseña al nivel: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```
## Solución
```bash
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | tar xO | bzcat | tar xO | zcat
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
bandit12@bandit:~$
```
## Notas Adicionales
Version corta, se descomprimió el archivo 8 veces

```
Algunos tipos de compresion en Linux
-----------------------------------------------------
ext comp desc     ver en consola
-----------------------------------------------------
.gz gzip gzip -d (gunzip) zcat
.bz2 bzip2 bzip2 -d (bunzip2) bzcat
.tar tar tar xf tar xO
----------------------------------------------------

otros (instalar) :
.zip zip unzip (7z x)
.rar rar unrar (7z x)
```
## Referencias
[Hex dump on Wikipedia](https://en.wikipedia.org/wiki/Hex_dump)