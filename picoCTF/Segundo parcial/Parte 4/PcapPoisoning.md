## Objetivo
How about some hide and seek heh?Download this [file](https://artifacts.picoctf.net/c/377/trace.pcap) and find the flag.
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF/pcappoisinin]
└─$ wireshark trace.pcap      
 ---- en wireshark no salio nada hasta el paquete 507
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/pcappoisinin]
└─$ strings trace.pcap | grep pico
picoCTF{P64P_4N4L7S1S_SU55355FUL_31010c46}F~
                                                                    
```
## Notas Adicionales

## Referencias
