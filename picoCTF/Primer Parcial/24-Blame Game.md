## Objetivo
Someone's commits seems to be preventing the program from working. Who is it?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/73/challenge.zip)
## Solución
```bash
victormcm-picoctf@webshell:~$ ls
challenge.zip  drop-in
victormcm-picoctf@webshell:~/drop-in$ git log
commit 5241c8d33658ddbc1410eae9eedb9713d4b996fd
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:09:11 2024 +0000

    important business work

commit fadeca9476b6713ec8cdda633aca9e9aebffc698
Author: picoCTF{@sk_th3_1nt3rn_e9957ce1} <ops@picoctf.com>
Date:   Sat Mar 9 21:09:11 2024 +0000

    optimize file size of prod code

```
## Notas Adicionales
git log - revisa los cambios que se han echo a la rama
## Referencias
