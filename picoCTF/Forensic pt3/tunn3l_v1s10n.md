## Objetivo
We found this [file](https://mercury.picoctf.net/static/7b2d7c26630e977197022d0af09e3aeb/tunn3l_v1s10n). Recover the flag.
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ exiftool tunn3l_v1s10n 
ExifTool Version Number         : 12.76
File Name                       : tunn3l_v1s10n
Directory                       : .
File Size                       : 2.9 MB
File Modification Date/Time     : 2021:03:15 14:24:47-04:00
File Access Date/Time           : 2024:10:09 12:27:45-04:00
File Inode Change Date/Time     : 2024:10:09 12:27:18-04:00
File Permissions                : -rw-rw-r--
File Type                       : BMP
File Type Extension             : bmp
MIME Type                       : image/bmp
BMP Version                     : Unknown (53434)
Image Width                     : 1134
Image Height                    : 306
Planes                          : 1
Bit Depth                       : 24
Compression                     : None
Image Length                    : 2893400
Pixels Per Meter X              : 5669
Pixels Per Meter Y              : 5669
Num Colors                      : Use BitDepth
Num Important Colors            : All
Red Mask                        : 0x27171a23
Green Mask                      : 0x20291b1e
Blue Mask                       : 0x1e212a1d
Alpha Mask                      : 0x311a1d26
Color Space                     : Unknown (,5%()
Rendering Intent                : Unknown (826103054)
Image Size                      : 1134x306
Megapixels                      : 0.347
┌──(kali㉿kali)-[~/picoCTF]
└─$ xxd -l 100  tunn3l_v1s10n 
00000000: 424d 8e26 2c00 0000 0000 bad0 0000 bad0  BM.&,...........
00000010: 0000 6e04 0000 3201 0000 0100 1800 0000  ..n...2.........
00000020: 0000 5826 2c00 2516 0000 2516 0000 0000  ..X&,.%...%.....
00000030: 0000 0000 0000 231a 1727 1e1b 2920 1d2a  ......#..'..) .*
00000040: 211e 261d 1a31 2825 352c 2933 2a27 382f  !.&..1(%5,)3*'8/
00000050: 2c2f 2623 332a 262d 2420 3b32 2e32 2925  ,/&#3*&-$ ;2.2)%
00000060: 3027 2333                                0'#3
                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ hexeditor tunn3l_v1s10n 

```

![[Pasted image 20241009104333.png]]

![[Pasted image 20241009104357.png]]

## Notas Adicionales
hexeditor edita los hexadecimales de un archivo
## Referencias
https://en.wikipedia.org/wiki/BMP_file_format