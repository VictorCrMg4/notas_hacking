## Objetivo
The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
## Datos De Acceso al Nivel

```
Servidor: bandit11@bandit.labs.overthewire.org -p 2220
Contraseña al nivel: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
## Solución
### Forma 1

```bash
bandit11@bandit:~$ cat data.txt | tr [a-zA-Z] [n-za-mN-ZA-M]
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
bandit11@bandit:~$
```
### Forma 2
CyberChef
![[Pasted image 20240828191635.png]]
## Notas Adicionales
rot13 - rota los caracteres  13 posiciones en el alfabeto
## Referencias
[Rot13 on Wikipedia](https://en.wikipedia.org/wiki/ROT13)