## Objetivo
Decode this [message](https://jupiter.challenges.picoctf.org/static/fc1edf07742e98a480c6aff7d2546107/message.wav) from the moon.
## Solución
```bash
┌──(kali㉿kali)-[/opt]
└─$ sudo git clone https://github.com/colaclanth/sstv.git 
[sudo] password for kali: 
Cloning into 'sstv'...
remote: Enumerating objects: 221, done.
remote: Counting objects: 100% (59/59), done.
remote: Compressing objects:  10% (1/10remote: Compressing objects:  20% (2/10remote: Compressing objects:  30% (3/10remote: Compressing objects:  40% (4/10remote: Compressing objects:  50% (5/10remote: Compressing objects:  60% (6/10remote: Compressing objects:  70% (7/10remote: Compressing objects:  80% (8/10remote: Compressing objects:  90% (9/10remote: Compressing objects: 100% (10/1remote: Compressing objects: 100% (10/10), done.
remote: Total 221 (delta 51), reused 49 (delta 49), pack-reused 162 (from 1)
Receiving objects: 100% (221/221), 1.01 MiB | 2.17 MiB/s, done.
Resolving deltas: 100% (139/139), done.
┌──(kali㉿kali)-[/opt/sstv]
└─$ sudo python setup.py install
running install
/usr/lib/python3/dist-packages/setuptools/_distutils/cmd.py:66: SetuptoolsDeprecationWarning: setup.py install is deprecated.
!!

        ** 
┌──(kali㉿kali)-[~/picoCTF]
└─$ sstv -d message.wav -o flag.jpg  
[sstv] Searching for calibration header... Found!    
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...   [###############################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ ls            
flag.jpg  message.wav
                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ open flag.jpg 

```
![[Pasted image 20241007103132.png]]
## Notas Adicionales

## Referencias

https://github.com/colaclanth/sstv