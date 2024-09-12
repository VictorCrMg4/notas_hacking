## Objetivo
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 4427`.
## Solución
```bash

victormcm-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 4427 
I don't think this is a flag either
This is defintely not a flag
Not a flag either
I don't think this is a flag either
I don't think this is a flag either
Not a flag either
I don't think this is a flag either
Not a flag either
I don't think this is a flag either
Not a flag either
Not a flag either
Again, I really don't think this is a flag
This is defintely not a flag
This is defintely not a flag
...

victormcm-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 4427 | grep pico
picoCTF{digital_plumb3r_5ea1fbd7}

```
## Notas Adicionales
grep nos ayuda encontrar cadenas que coincidan con el argumento
## Referencias