## Objetivo
The password for the next level is stored in a file called **spaces in this filename** located in the home directory
## Datos De Acceso al Nivel
```
Servidor: bandit2@bandit.labs.overthewire.org -p 2220
Contraseña del nivel: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```
## Solución
```bash
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat "spaces in this filename"
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
bandit2@bandit:~$
```
## Notas Adicionales
ls	- lista de los archivos de la carpeta actual
cd/ - me lleva al directorio raíz
cat - muestra el contenido de varios archivos en la salida estándar
file - se utiliza para determinar el tipo de archivo mediante su contenido
find - se utiliza para buscar archivos y directorios en una jerarquía de directorios determinada
Si el nombre del archivo contiene espacios 
- Usar diagonal en el espacio archivo\ con\ espacios
- Delimitar el nombre con "
## Referencias
[Google Search for “spaces in filename”](https://www.google.com/search?q=spaces+in+filename)