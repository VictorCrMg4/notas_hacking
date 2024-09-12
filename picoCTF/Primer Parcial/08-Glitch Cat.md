## Objetivo

Our flag printing service has started glitching!`$ nc saturn.picoctf.net 61422`
## Solución
```bash
victormcm-picoctf@webshell:~$ nc saturn.picoctf.net 61422
'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
^C
victormcm-picoctf@webshell:~$ python3
Python 3.10.12 (main, Nov 20 2023, 15:14:05) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
'picoCTF{gl17ch_m3_n07_bda68f75}'
>>> 
```
## Notas Adicionales
python suma valores ASCII
## Referencias
