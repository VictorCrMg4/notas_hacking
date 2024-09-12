## Objetivo
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/70/challenge.zip)

## Solución
```bash
victormcm-picoctf@webshell:~/drop-in$ ls
challenge.zip  drop-in
victormcm-picoctf@webshell:~/drop-in$ cd drop-in/     
victormcm-picoctf@webshell:~/drop-in/drop-in$ ls
flag.py
victormcm-picoctf@webshell:~/drop-in/drop-in$ git branch -a
victormcm-picoctf@webshell:~/drop-in/drop-in$ git checkout 
HEAD             feature/part-2   main 
feature/part-1   feature/part-3   
victormcm-picoctf@webshell:~/drop-in/drop-in$ python flag.py 
Printing the flag...
picoCTF{t3@mw0rk_
victormcm-picoctf@webshell:~/drop-in/drop-in$ git checkout feature/part-1
Switched to branch 'feature/part-1'
victormcm-picoctf@webshell:~/drop-in/drop-in$ ls
flag.py
victormcm-picoctf@webshell:~/drop-in/drop-in$ python flag.py
Printing the flag...
victormcm-picoctf@webshell:~/drop-in/drop-in$ git branch -a
victormcm-picoctf@webshell:~/drop-in/drop-in$ git checkout feature/part-2
Switched to branch 'feature/part-2'
victormcm-picoctf@webshell:~/drop-in/drop-in$ python 
.git/    flag.py  
victormcm-picoctf@webshell:~/drop-in/drop-in$ python flag.py 
Printing the flag...
victormcm-picoctf@webshell:~/drop-in/drop-in$ git checkout feature/part-3
Switched to branch 'feature/part-3'
victormcm-picoctf@webshell:~/drop-in/drop-in$ python flag.py 
Printing the flag...
w0rk_7ffa0077}
victormcm-picoctf@webshell:~/drop-in/drop-in$ 


```
## Notas Adicionales

## Referencias
