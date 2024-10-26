## Objetivo
Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/149ab4b27d16922142a1e8381677d76f/cat.jpg)
## Solución
![[Pasted image 20241021234321.png]]

```bash
┌──(kali㉿kali)-[~/picoCTF/information]
└─$ file cat.jpg
cat.jpg: JPEG image data, JFIF standard 1.02, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 2560x1598, components 3
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/information]
└─$ exiftool cat.jpg 
ExifTool Version Number         : 12.76
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2021:03:15 14:24:46-04:00
File Access Date/Time           : 2024:10:22 01:41:45-04:00
File Inode Change Date/Time     : 2024:10:22 01:41:42-04:00
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                 
```
- Notamos que el metadato `Current IPTC Digest` esta escrito en base64 por lo que lo decodificamos.
```bash
┌──(kali㉿kali)-[~/picoCTF/information]
└─$ echo 7a78f3d9cfb1ce42ab5a3aa30573d617 | base64 -d
picoCTF{the_m3tadata_1s_modified}
���w}q��q�6i�Zݦ�Ӟ�w�{picoCTF{the_m3tadata_1s_modified}: command not found

```

## Notas Adicionales
## Referencias
