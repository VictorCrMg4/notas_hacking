## Objetivo
Can you make sense of this file?Download the file [here](https://artifacts.picoctf.net/c/472/enc_flag).
## Solución
```bash
victormcm-picoctf@webshell:~$ ls
enc_flag
victormcm-picoctf@webshell:~$ base64 -d enc_flag | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d
picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_73494190}
```
## Notas Adicionales

## Referencias