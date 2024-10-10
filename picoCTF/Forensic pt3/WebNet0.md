## Objetivo
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key). Recover the flag.
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ wireshark capture.pcap &

```
Edit > preferences > protocols > TLS > RSA keys list y meter picopico.key

![[Pasted image 20241009110853.png]]
picoCTF{nongshim.shrimp.crackers}


## Forma 2
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ ssldump -r capture.pcap -k picopico.key -d | grep pico -A 2
Short read: -1295 bytes available (expecting 2)
Short read: -1295 bytes available (expecting 2)
Short read: -1295 bytes available (expecting 2)
    61 67 3a 20 70 69 63 6f 43 54 46 7b 6e 6f 6e 67    ag: picoCTF{nong
    73 68 69 6d 2e 73 68 72 69 6d 70 2e 63 72 61 63    shim.shrimp.crac
    6b 65 72 73 7d 0d 0a 43 6f 6e 74 65 6e 74 2d 4c    kers}..Content-L
--
    67 3a 20 70 69 63 6f 43 54 46 7b 6e 6f 6e 67 73    g: picoCTF{nongs
    68 69 6d 2e 73 68 72 69 6d 70 2e 63 72 61 63 6b    him.shrimp.crack
    65 72 73 7d 0d 0a 43 6f 6e 74 65 6e 74 2d 4c 65    ers}..Content-Le
            
```

## Notas Adicionales
ssldump analiza y depura el tráfico de conexiones SSL/TLS.
## Referencias
