## Objetivo
The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

## Datos De Acceso al Nivel
``` 
Servidor: bandit8@bandit.labs.overthewire.org -p 2220
Constraseña del nivel:dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```
## Solución
```bash
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```
## Notas Adicionales
sort data.txt | uniq -u
	sort - ordena las lineas de texto
	uniq - filtra la lineas que no se repiten
## Referencias
[Piping and Redirection](https://ryanstutorials.net/linuxtutorial/piping.php)