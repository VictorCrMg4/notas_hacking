## Objetivo
This file has a flag in plain sight (aka "in-the-clear"). [Download flag](https://mercury.picoctf.net/static/0e428b2db9788d31189329bed089ce98/flag).
## Solución
```bash
victormcm-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/0e428b2db9788d31189329bed089ce98/flag
--2024-09-11 16:45:28--  https://mercury.picoctf.net/static/0e428b2db9788d31189329bed089ce98/flag
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34 [application/octet-stream]
Saving to: 'flag'

flag              100%[==========>]      34  --.-KB/s    in 0s      

2024-09-11 16:45:28 (2.49 MB/s) - 'flag' saved [34/34]

victormcm-picoctf@webshell:~$ ls
flag
victormcm-picoctf@webshell:~$ cat flag 
picoCTF{s4n1ty_v3r1f13d_2fd6ed29}
victormcm-picoctf@webshell:~$ 
```
## Notas Adicionales

## Referencias
