## Objetivo
Download this image and find the flag.

- [Download image](https://artifacts.picoctf.net/c/215/pico.flag.png)
## Solución

Imagen que aparentemente no esconde nada ![[Pasted image 20241018215127.png]]

```bash
──(kali㉿kali)-[~/picoCTF/redgonwrong]
└─$ zsteg -a pico.flag.png | grep pico
b1,rgb,lsb,xy       .. text: "picoCTF{7h3r3_15_n0_5p00n_96ae0ac1}$t3g0"

```
## Notas Adicionales

## Referencias
