## Objetivo
The password for the next level is stored in the file **data.txt**, which contains base64 encoded data
## Datos De Acceso al Nivel
``` 
Servidor: bandit10@bandit.labs.overthewire.org -p 2220
Constraseña del nivel:FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```
## Solución
```bash
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
bandit10@bandit:~$ echo "chilaquiles"
chilaquiles
bandit10@bandit:~$ echo "chilaquiles" | base64
Y2hpbGFxdWlsZXMK
bandit10@bandit:~$ cat data.txt | base64 -d
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
bandit10@bandit:~$
```
## Notas Adicionales
base64 es un esquema de codificacion de binario a texto, AZaz09+=/
## Referencias
[Base64 on Wikipedia](https://en.wikipedia.org/wiki/Base64)
https://gchq.github.io/CyberChef/