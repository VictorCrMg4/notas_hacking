## Objetivo
Using netcat (nc) is going to be pretty important. Can you connect to `jupiter.challenges.picoctf.org` at port `41120` to get the flag?
## Solución
```bash
victormcm-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org  41120
You're on your way to becoming the net cat master
picoCTF{nEtCat_Mast3ry_3214be47}
```
## Notas Adicionales
The **nc** (or **netcat**) utility is used for just about anything under the sun involving TCP or UDP. It can open TCP connections, send UDP packets, listen on arbitrary TCP and UDP ports, do port scanning, and deal with both IPv4 and IPv6
## Referencias
https://linux.die.net/man/1/nc
