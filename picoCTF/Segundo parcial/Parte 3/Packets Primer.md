## Objetivo
Download the packet capture file and use packet analysis software to find the flag.

- [Download packet capture](https://artifacts.picoctf.net/c/194/network-dump.flag.pcap)
## Solución

```bash
┌──(kali㉿kali)-[~/picoCTF/information]
└─$ file network-dump.flag.pcap 
network-dump.flag.pcap: pcap capture file, microsecond ts (little-endian) - version 2.4 (Ethernet, capture length 262144)
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/information]
└─$ wireshark network-dump.flag.pcap &

```
- Abrimos el archivo con wireshark, seleccionamos un archivo que información y le damos clic derecho > Follow > TCP Steam; y despues nos mostrara la bandera.
```bash
p i c o C T F { p 4 c k 3 7 _ 5 h 4 r k _ b 9 d 5 3 7 6 5 }
picoCTF{p4ck37_5h4rk_b9d53765}
```


## Notas Adicionales
## Referencias