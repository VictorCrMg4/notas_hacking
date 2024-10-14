## Objetivo
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ mmls disk.flag.img       
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000360447   0000153600   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000360448   0000614399   0000253952   Linux (0x83)
┌──(kali㉿kali)-[~/picoCTF]
└─$ fls -o 360448 disk.flag.img -r 3981
r/r * 2082(realloc):    flag.txt
r/r 2371:       flag.uni.txt
                                                                                
┌──(kali㉿kali)-[~/picoCTF]
└─$ icat -o 360448 disk.flag.img 2363
apk add nano
mkdir my_folder
cd my_folder/
nano flag.txt
ls -al
iconv -f ascii -t utf16 > flag.uni.txt
l
ls -al
iconv -f ascii -t utf16 flag.txt > flag.uni.txt
ls -al
shred
shred -zu flag.txt 
ls -al
halt
                                                                                
┌──(kali㉿kali)-[~/picoCTF]
└─$ icat -o 360448 disk.flag.img 2371
picoCTF{by73_5urf3r_2f22df38}

```
## Notas Adicionales

## Referencias