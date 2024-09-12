## Objetivo
Fix the syntax error in the Python script to print the flag.
## Solución
```bash
victormcm-picoctf@webshell:~$ ls
README.txt  fixme1.py  fixme2.py
victormcm-picoctf@webshell:~$ python fixme2.py
  File "/home/victormcm-picoctf/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
victormcm-picoctf@webshell:~$ nano fixme2.py
victormcm-picoctf@webshell:~$ python fixme2.py
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_e8814d03}
```
## Notas Adicionales

## Referencias
