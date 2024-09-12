## Objetivo
Unzip this archive and find the flag.
## Solución
```bash
victormcm-picoctf@webshell:~$ unzip big-zip-files.zip 
...
...
...
victormcm-picoctf@webshell:~$ ls
README.txt  big-zip-files  big-zip-files.zip
victormcm-picoctf@webshell:~$ grep -r "pico" big-zip-files
big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```
## Notas Adicionales
grep - buscar palabras claves
## Referencias
