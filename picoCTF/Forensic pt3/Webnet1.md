
## Objetivo

## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ wireshark capture.pcap &
[3] 31385
           
```
Checamos que hay una imagen
File > Export objects > HTTP > vultures.jpg
```bash
                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ strings vulture.jpg | grep pico                            
picoCTF{honey.roasted.peanuts}

```
![[Pasted image 20241009112208.png]]
## Notas Adicionales

## Referencias
