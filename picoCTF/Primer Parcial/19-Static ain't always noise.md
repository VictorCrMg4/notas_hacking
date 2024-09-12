## Objetivo
Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/0f6ea599582dcce7b4f1ba94e3617baf/static)? This [BASH script](https://mercury.picoctf.net/static/0f6ea599582dcce7b4f1ba94e3617baf/ltdis.sh) might help!
## Solución 
```bash
victormcm-picoctf@webshell:~$ ls
ltdis.sh  static
victormcm-picoctf@webshell:~$ strings static | grep pico
picoCTF{d15a5m_t34s3r_6f8c8200}
```


## Notas Adicionales
strings -permite extraer texto dentro de un archivo binario o de datos.
## Referencias
