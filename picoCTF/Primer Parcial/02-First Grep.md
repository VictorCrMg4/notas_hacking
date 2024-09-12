## Objetivo
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/515f19f3612bfd97cd3f0c0ba32bd864/file)? This would be really tedious to look through manually, something tells me there is a better way.
## Solución
```bash
victormcm-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/515f19f3612bfd97cd3f0c0ba32bd864/file
--2024-09-09 17:19:58--  https://jupiter.challenges.picoctf.org/static/515f19f3612bfd97cd3f0c0ba32bd864/file
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14551 (14K) [application/octet-stream]
Saving to: 'file'

file              100%[============>]  14.21K  --.-KB/s    in 0s      

2024-09-09 17:19:58 (356 MB/s) - 'file' saved [14551/14551]

victormcm-picoctf@webshell:~$ grep picoCTF file
picoCTF{grep_is_good_to_find_things_5af9d829}
victormcm-picoctf@webshell:~$ 
```
## Notas Adicionales

## Referencias
