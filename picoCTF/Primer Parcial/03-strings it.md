## Objetivo
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings) without running it?
## Solución
```bash
victormcm-picoctf@webshell:~$ strings -n 15 strings | grep pico
picoCTF{5tRIng5_1T_7f766a23}
victormcm-picoctf
```
## Notas Adicionales
strings - permite obtener las cadenas de texto que hay en un archivo binario
## Referencias