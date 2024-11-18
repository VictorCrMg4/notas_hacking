## Objetivo
The password for the next level is stored in a hidden file in the **inhere** directory.
## Datos De Acceso al Nivel
```
Servidor: bandit3@bandit.labs.overthewire.org -p 2220
Contraseña del nivel: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

## Solución
```bash
bandit3@bandit:~$ ls -la
total 24
drwxr-xr-x  3 root root 4096 Jul 17 15:57 .
drwxr-xr-x 70 root root 4096 Jul 17 15:58 ..
-rw-r--r--  1 root root  220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root root 3771 Mar 31 08:41 .bashrc
drwxr-xr-x  2 root root 4096 Jul 17 15:57 inhere
-rw-r--r--  1 root root  807 Mar 31 08:41 .profile
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 Jul 17 15:57 .
drwxr-xr-x 3 root    root    4096 Jul 17 15:57 ..
-rw-r----- 1 bandit4 bandit3   33 Jul 17 15:57 ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
bandit3@bandit:~/inhere$
```
## Notas Adicionales
ls	-a lista de los archivos de la carpeta actual en formato largo y muestra los archivos ocultos
cd/ - me lleva al directorio raíz
cat - muestra el contenido de varios archivos en la salida estándar
file - se utiliza para determinar el tipo de archivo mediante su contenido
find - se utiliza para buscar archivos y directorios en una jerarquía de directorios determinada
## Referencias
