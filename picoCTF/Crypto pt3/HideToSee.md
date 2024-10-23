## Objetivo
How about some hide and seek heh? Look at this image [here](https://artifacts.picoctf.net/c/241/atbash.jpg).
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF/crypto]
└─$ steghide --extract -sf atbash.jpg
Enter passphrase: 
wrote extracted data to "encrypted.txt".
```
![[Pasted image 20241023114404.png]]
```bash                                                 
┌──(kali㉿kali)-[~/picoCTF/crypto]
└─$ cat encrypted.txt 
krxlXGU{zgyzhs_xizxp_7142uwv9}

```

![[Pasted image 20241023114503.png]]

```
picoCTF{atbash_crack_7142fde9}
```
## Notas Adicionales

## Referencias
