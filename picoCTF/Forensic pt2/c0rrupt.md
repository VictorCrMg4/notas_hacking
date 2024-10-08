## Objetivo
We found this [file](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery). Recover the flag.
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ xxd mystery | head 
00000000: 8965 4e34 0d0a b0aa 0000 000d 4322 4452  .eN4........C"DR
00000010: 0000 066a 0000 0447 0802 0000 007c 8bab  ...j...G.....|..
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 aa00 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f0aa aaff a5ab 4445 5478 5eec bd3f  R$......DETx^..?
00000060: 8e64 cd71 bd2d 8b20 2080 9041 8302 08d0  .d.q.-.  ..A....
00000070: f9ed 40a0 f36e 407b 9023 8f1e d720 8b3e  ..@..n@{.#... .>
00000080: b7c1 0d70 0374 b503 ae41 6bf8 bea8 fbdc  ...p.t...Ak.....
00000090: 3e7d 2a22 336f de5b 55dd 3d3d f920 9188  >}*"3o.[U.==. ..
┌──(kali㉿kali)-[~/picoCTF]
└─$ hexeditor mystery  

```
Modificamos los hexadecimales de la imagen para reparar la imagen
```
File: mystery                      ASCII Offset: 0x00000000 / 0x000318BB (%00)   
00000000  89 50 4E 47  0D 0A 1A 0A   00 00 00 0D  49 48 44 52    .PNG........IHDR
00000010  00 00 06 6A  00 00 04 47   08 02 00 00  00 7C 8B AB    ...j...G.....|..
00000020  78 00 00 00  01 73 52 47   42 00 AE CE  1C E9 00 00    x....sRGB.......
00000030  00 04 67 41  4D 41 00 00   B1 8F 0B FC  61 05 00 00    ..gAMA......a...
00000040  00 09 70 48  59 73 00 00   16 25 00 00  16 25 01 49    ..pHYs...%...%.I
00000050  52 24 F0 00  00 FF A5 49   44 41 54 78  5E EC BD 3F    R$.....IDATx^..?
00000060  8E 64 CD 71  BD 2D 8B 20   20 80 90 41  83 02 08 D0    .d.q.-.  ..A....
00000070  F9 ED 40 A0  F3 6E 40 7B   90 23 8F 1E  D7 20 8B 3E    ..@..n@{.#... .>
00000080  B7 C1 0D 70  03 74 B5 03   AE 41 6B F8  BE A8 FB DC    ...p.t...Ak.....
00000090  3E 7D 2A 22  33 6F DE 5B   55 DD 3D 3D  F9 20 91 88    >}*"3o.[U.==. ..
000000A0  38 71 22 32  EB 4F 57 CF   14 E6 25 FF  E5 FF 5B 2C    8q"2.OW...%...[,
000000B0  16 8B C5 62  B1 58 2C 16   8B C5 62 B1  58 2C 16 1D    ...b.X,...b.X,..
000000C0  D6 D7 67 8B  C5 62 B1 58   2C 16 8B C5  62 B1 58 2C    ..g..b.X,...b.X,
000000D0  16 8B 45 97  F5 F5 D9 62   B1 58 2C 16  8B C5 62 B1    ..E....b.X,...b.
000000E0  58 2C 16 8B  C5 62 D1 65   7D 7D B6 58  2C 16 8B C5    X,...b.e}}.X,...
000000F0  62 B1 58 2C  16 8B C5 62   B1 58 74 59  5F 9F 2D 16    b.X,...b.XtY_.-.
00000100  8B C5 62 B1  58 2C 16 8B   C5 62 B1 58  2C 16 5D D6    ..b.X,...b.X,.].
00000110  D7 67 8B C5  62 B1 58 2C   16 8B C5 62  B1 58 2C 16    .g..b.X,...b.X,.
00000120  8B 45 97 F5  F5 D9 62 B1   58 2C 16 8B  C5 62 B1 58    .E....b.X,...b.X
00000130  2C 16 8B C5  62 D1 65 7D   7D B6 58 2C  16 8B C5 62    ,...b.e}}.X,...b
```

```bash

                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ pngcheck -v mystery
zlib warning:  different version (expected 1.2.13, using 1.3.1)

File: mystery (202940 bytes)
  chunk IHDR at offset 0x0000c, length 13
    1642 x 1095 image, 24-bit RGB, non-interlaced
  chunk sRGB at offset 0x00025, length 1
    rendering intent = perceptual
  chunk gAMA at offset 0x00032, length 4: 0.45455
  chunk pHYs at offset 0x00042, length 9: 5669x5669 pixels/meter (144 dpi)
  chunk IDAT at offset 0x00057, length 65445
    zlib: deflated, 32K window, fast compression
  chunk IDAT at offset 0x10008, length 65524
  chunk IDAT at offset 0x20008, length 65524
  chunk IDAT at offset 0x30008, length 6304
  chunk IEND at offset 0x318b4, length 0
No errors detected in mystery (9 chunks, 96.3% compression).
                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ open  mystery    
           
```
![[Pasted image 20241007112504.png]]

## Notas Adicionales
**PNG** (siglas en inglés de _**Portable Network Graphics**_, **Gráficos de Red Portátiles**) es un [formato gráfico](https://es.wikipedia.org/wiki/Formatos_gr%C3%A1ficos "Formatos gráficos") basado en un [algoritmo de compresión sin pérdida](https://es.wikipedia.org/wiki/Algoritmo_de_compresi%C3%B3n_sin_p%C3%A9rdida "Algoritmo de compresión sin pérdida") para [bitmaps](https://es.wikipedia.org/wiki/Bitmap "Bitmap") no sujeto a [patentes](https://es.wikipedia.org/wiki/Patente "Patente").

## Referencias
https://en.wikipedia.org/wiki/List_of_file_signatures
