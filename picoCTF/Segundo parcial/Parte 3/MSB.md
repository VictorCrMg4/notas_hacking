## Objetivo
This image passes LSB statistical analysis, but we can't help but think there must be something to the visual artifacts present in this image... Download the image [here](https://artifacts.picoctf.net/c/301/Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png)
## Solución
Descargamos la imagen 
![[Pasted image 20241022001004.png]]
Abrimos la imagen con stegsolver
```bash
┌──(kali㉿kali)-[~/picoCTF/bin]
└─$ java -jar stegsolve.jar         
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
```

![[Pasted image 20241022001517.png]]

Seleccionamos para cmabiar los valores de los bits que correpsonde a los colores rojo verde y azul.

Guardamos el texto que sale en la previsualización.

Abrimos los el archivo que extrajimos y buscamos la la palabra pico que es parte de la bandera.
```bash

┌──(kali㉿kali)-[~/picoCTF]
└─$ cat flag.txt | grep pico
220a7069636f4354 467b31355f793075  ".picoCT F{15_y0u
                                                                                        
┌──(kali㉿kali)-[~/picoCTF]
└─$ open flag.txt 

```

```

068652077617320 626f756e6420746f   he was  bound to
20646f2c20616e64 20646f6573206e6f   do, and  does no
7420646573657276 6520667572746865  t deserv e furthe
720a70756e697368 6d656e7420756e6c  r.punish ment unl
6573732068652063 6f6d6d6974732073  ess he c ommits s
6f6d65206e657720 6f6666656e63652e  ome new  offence.
220a7069636f4354 467b31355f793075  ".picoCT F{15_y0u
725f71756535375f 7175317830373163  r_que57_ qu1x071c
5f30725f68337230 31635f3361323139  _0r_h3r0 1c_3a219
3137347d0a0a2254 686f752068617374  174}.."T hou hast
2073616964207765 6c6c20616e642068   said we ll and h
6974207468652070 6f696e742c222061  it the p oint," a
6e73776572656420 446f6e2051756978  nswered  Don Quix
6f74653b20616e64 20736f20490a7265  ote; and  so I.re



picoCTF{15_y0ur_que57_ qu1x071c_0r_h3r01c_3a219174}
```
## Notas Adicionales
## Referencias
