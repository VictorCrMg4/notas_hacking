## Objetivo
A Traffic from an unknown user has been captured, analyze this capture and find out what happened

Remember to use the flag format: flagmx{XXXX}
## Solución
```bash
┌──(kali㉿kali)-[~/MetaRedCTF]
└─$ wireshark r4.pcap

┌──(kali㉿kali)-[~/MetaRedCTF]
└─$ open r3.png

┌──(kali㉿kali)-[~/MetaRedCTF]
└─$ 7z e r2.7z
7-Zip 24.08 (x64) : Copyright (c) 1999-2024 Igor Pavlov : 2024-08-11
64-bit locale=en_US.UTF-8 Threads:2 OPEN_MAX:1024
Scanning the drive for archives:
1 file, 222 bytes (1 KiB)
Extracting archive: r2.7z
Enter password (will not be echoed): 5688722

--

Path = r2.7z
Type = 7z
Physical Size = 222
Headers Size = 190
Method = LZMA2:12 7zAES
Solid = -
Blocks = 1
Everything is Ok
Size:
16
Compressed: 222

┌──(kali㉿kali)-[~/MetaRedCTF]
└─$ cat r1.txt

flagmx{cuv4v3}
```
## Notas Adicionales

## Referencias
