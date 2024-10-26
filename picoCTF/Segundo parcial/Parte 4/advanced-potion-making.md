## Objetivo
Ron just found his own copy of advanced potion making, but its been corrupted by some kind of spell. Help him recover it!
## Solución
Nos dicen que el archivo esta corrupto asi que vemos sus hexadecimales y vemos que su firma y otro hexadecimales no concuerdan con los de una imagen png normal

```
file: advanced-potion-making       ASCII Offset: 0x00000000 / 0x000076A3 (%00)   
00000000  89 50 42 11  0D 0A 1A 0A   00 12 13 14  49 48 44 52    .PB.........IHDR
00000010  00 00 09 90  00 00 04 D8   08 02 00 00  00 04 2D E7    ..............-.
00000020  78 00 00 00  01 73 52 47   42 00 AE CE  1C E9 00 00    x....sRGB.......
00000030  00 04 67 41  4D 41 00 00   B1 8F 0B FC  61 05 00 00    ..gAMA......a...
00000040  00 09 70 48  59 73 00 00   16 25 00 00  16 25 01 49    ..pHYs...%...%.I
00000050  52 24 F0 00  00 76 39 49   44 41 54 78  5E EC FD 61    R$...v9IDATx^..a
00000060  72 E3 4C 94  A6 59 CE 16   6A FE 76 CD  FE 57 D7 DD    r.L..Y..j.v..W..
00000070  5B 18 45 E9  4B 8A 7A 28   D1 9D 20 48  07 A9 63 76    [.E.K.z(.. H..cv
00000080  AC 2D 2B 3E  BF AF 5F 07   18 01 82 D7  B2 F3 FF F3    .-+>.._.........
00000090  FF FC 7F FF  7F 00 00 00   00 00 00 00  4B 18 58 02    ............K.X.
000000A0  00 00 00 00  00 00 CB 18   58 02 00 00  00 00 00 00    ........X.......
000000B0  CB 18 58 02  00 00 00 00   00 00 CB 18  58 02 00 00    ..X.........X...
000000C0  00 00 00 00  CB 18 58 02   00 00 00 00  00 00 CB 18    ......X.........
000000D0  58 02 00 00  00 00 00 00   CB 18 58 02  00 00 00 00    X.........X.....
000000E0  00 00 CB 18  58 02 00 00   00 00 00 00  CB 18 58 02    ....X.........X.
000000F0  00 00 00 00  00 00 CB 18   58 02 00 00  00 00 00 00    ........X.......
00000100  CB 18 58 02  00 00 00 00   00 00 CB 18  58 02 00 00    ..X.........X...
00000110  00 00 00 00  CB 18 58 02   00 00 00 00  00 00 CB 18    ......X.........
00000120  58 02 00 00  00 00 00 00   CB 18 58 02  00 00 00 00    X.........X.....
00000130  00 00 CB 18  58 02 00 00   00 00 00 00  CB 18 58 02    ....X.........X.
00000140  00 00 00 00  00 00 CB 18   58 02 00 00  00 00 00 00    ........X.......
00000150  CB 18 58 02  00 00 00 00   00 00 CB 18  58 02 00 00    ..X.........X...
00000160  00 00 00 00  CB 18 58 02   00 00 00 00  00 00 CB 18    ......X.........
00000170  58 02 00 00  00 00 00 00   CB 18 58 02  00 00 00 00    X.........X.....

```
Cambiamos los bytes
```
ile: advanced-potion-making       ASCII Offset: 0x00000000 / 0x000076A3 (%00)   
00000000  89 50 4E 47  0D 0A 1A 0A   00 00 00 0D  49 48 44 52    .PNG........IHDR
00000010  00 00 09 90  00 00 04 D8   08 02 00 00  00 04 2D E7    ..............-.
00000020  78 00 00 00  01 73 52 47   42 00 AE CE  1C E9 00 00    x....sRGB.......
00000030  00 04 67 41  4D 41 00 00   B1 8F 0B FC  61 05 00 00    ..gAMA......a...
00000040  00 09 70 48  59 73 00 00   16 25 00 00  16 25 01 49    ..pHYs...%...%.I
00000050  52 24 F0 00  00 76 39 49   44 41 54 78  5E EC FD 61    R$...v9IDATx^..a
00000060  72 E3 4C 94  A6 59 CE 16   6A FE 76 CD  FE 57 D7 DD    r.L..Y..j.v..W..
00000070  5B 18 45 E9  4B 8A 7A 28   D1 9D 20 48  07 A9 63 76    [.E.K.z(.. H..cv
00000080  AC 2D 2B 3E  BF AF 5F 07   18 01 82 D7  B2 F3 FF F3    .-+>.._.........
00000090  FF FC 7F FF  7F 00 00 00   00 00 00 00  4B 18 58 02    ............K.X.
000000A0  00 00 00 00  00 00 CB 18   58 02 00 00  00 00 00 00    ........X.......
000000B0  CB 18 58 02  00 00 00 00   00 00 CB 18  58 02 00 00    ..X.........X...
000000C0  00 00 00 00  CB 18 58 02   00 00 00 00  00 00 CB 18    ......X.........
000000D0  58 02 00 00  00 00 00 00   CB 18 58 02  00 00 00 00
```

aparece una imagen en rojo

![[Pasted image 20241016235644.png]]
Instalamos stegsolver
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ wget http://www.caesum.com/handbook/Stegsolve.jar -O stegsolve.jar
--2024-10-17 02:00:30--  http://www.caesum.com/handbook/Stegsolve.jar
Resolving www.caesum.com (www.caesum.com)... 216.234.165.33
Connecting to www.caesum.com (www.caesum.com)|216.234.165.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 312271 (305K) [application/x-java-archive]
Saving to: ‘stegsolve.jar’

stegsolve.jar        100%[===================>] 304.95K   241KB/s    in 1.3s    

2024-10-17 02:00:32 (241 KB/s) - ‘stegsolve.jar’ saved [312271/312271]

                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ chmod +x stegsolve.jar

┌──(kali㉿kali)-[~/picoCTF/bin]
└─$ java -jar stegsolve.jar         
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true




```

Usamos estegsolver para que este encuentre el mensaje oculto
![[Pasted image 20241017000801.png]]
## Notas Adicionales

## Referencias
