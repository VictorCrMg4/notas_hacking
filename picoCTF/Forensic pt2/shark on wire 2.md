## Objetivo
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ wireshark capture.pcap &

```

![[Pasted image 20241007120023.png]]
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ nano expl.py  
```
exploit
```python
from scapy.all import *

packets = rdpcap('capture.pcap')
flag = ''
for p in packets:
        if UDP in p and p[UDP].dport ==22:
                if p[UDP].sport > 5000:
                        flag += chr(p[UDP].sport-5000)
print(flag)


```



```bash                                                                                                                                  ┌──(kali㉿kali)-[~/picoCTF]
└─$ python expl.py
picoCTF{p1LLf3r3d_data_v1a_st3g0}
                                    
```
## Notas Adicionales

## Referencias
