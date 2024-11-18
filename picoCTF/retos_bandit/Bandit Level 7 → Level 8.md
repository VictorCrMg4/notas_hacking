## Objetivo
The password for the next level is stored in the file **data.txt** next to the word **millionth**
## Datos De Acceso al Nivel
``` 
Servidor: bandit7@bandit.labs.overthewire.org -p 2220
Constraseña del nivel:morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```
## Solución
```bash
bandit7@bandit:~$ wc data.txt
  98567  197133 4184396 data.txt
bandit7@bandit:~$ wc -l data.txt
98567 data.txt
bandit7@bandit:~$ grep millionth data.txt
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```
## Notas Adicionales
wc -l - cuenta las lineas que tiene un archivo de texto.
grep - busca un patron en un grupo de palabras
	-n indica a grep indica a grep que mustra la linea

## Referencias