## Objetivo
There's something in the [building](https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png). Can you retrieve the flag?
## Solución 1
![[Pasted image 20241002111536.png]]
## Solución 2
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ sudo gem install zsteg   
....
┌──(kali㉿kali)-[~/picoCTF]
└─$ zsteg -a buildings.png | grep pico
b1,rgb,lsb,xy       .. text: "picoCTF{h1d1ng_1n_th3_b1t5}"

```
## Notas Adicionales

## Referencias
https://stylesuxx.github.io/steganography/
