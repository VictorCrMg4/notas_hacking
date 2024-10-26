## Objetivo
The flag is somewhere on this web application not necessarily on the website. Find it.Check [this](http://saturn.picoctf.net:62631/) out.
## Solución
Entramos al archivo robots.txt de la pagina:
```bash
http://saturn.picoctf.net:54106/robots.txt
```

Dentro del archivo no aparecerá los siguiente:
```bash
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/
```

Con la ayuda de CyberChef decodificamos el nombre del archivo con que esta escrito en base 64
```bash
anMvbXlmaWxlLnR4dA==

js/myfile.txt
```
Entramos a ese archivo:
```bash
http://saturn.picoctf.net:62631/js/myfile.txt
```
Ahí se encuentra la bandera:
```bash
picoCTF{Who_D03sN7_L1k5_90B0T5_718c9043}
```

## Notas Adicionales
## Referencias