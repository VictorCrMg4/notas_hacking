## Objetivo
Download this disk image, find the key and log into the remote machine.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download disk image](https://artifacts.picoctf.net/c/71/disk.img.gz)
- Remote machine: `ssh -i key_file -p 49909 ctf-player@saturn.picoctf.net`
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ mmls disk.img     
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000471039   0000264192   Linux (0x83)
                                                                                                                                                              
┌──(kali㉿kali)-[~/picoCTF]
└─$ ls
base_images    disk.img  flag.txt      ppt
disk.flag.img  docProps  flag.txt.enc  _rels
                                                                                
┌──(kali㉿kali)-[~/picoCTF]
└─$ fls -o 0000206848 disk.img 470 -r
r/r 2344:       .ash_history
d/d 3916:       .ssh
+ r/r 2345:     id_ed25519
+ r/r 2346:     id_ed25519.pub
                                                                                                                                        
┌──(kali㉿kali)-[~/picoCTF]
└─$ icat -o 0000206848 disk.img 2345
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
QyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLAAAAJgxpYKDMaWC
gwAAAAtzc2gtZWQyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLA
AAAECItu0F8DIjWxTp+KeMDvX1lQwYtUvP2SfSVOfMOChxYGCtd7hso2E7OQItY6aTjMMy
KZb1FVmeBfnVjyHcGYosAAAADnJvb3RAbG9jYWxob3N0AQIDBAUGBw==
-----END OPENSSH PRIVATE KEY-----
                                                                                
┌──(kali㉿kali)-[~/picoCTF]
└─$ icat -o 0000206848 disk.img 2345 > key_file
                                                                                
┌──(kali㉿kali)-[~/picoCTF]
└─$ chmod 600 key_file 
                                                                                                                                              
┌──(kali㉿kali)-[~/picoCTF]
└─$ ssh -i key_file -p 49909 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:49909 ([13.59.203.175]:49909)' can't be established.
ED25519 key fingerprint is SHA256:XBSvB1lk28EctsAVdKJtsl0A7C5bonqPrvHCYH8aEy4.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? y
Please type 'yes', 'no' or the fingerprint: yes
Warning: Permanently added '[saturn.picoctf.net]:49909' (ED25519) to the list of known hosts.
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@challenge:~$ flag.txt
-bash: flag.txt: command not found
ctf-player@challenge:~$ ls
flag.txt
ctf-player@challenge:~$ cat flag.txt 
picoCTF{k3y_5l3u7h_af277f77}ctf-player@challenge:~$ 

```
## Notas Adicionales
mmls: sirve para listar las particiones de un disco o imagen de disco, mostrando información detallada sobre el esquema de particionado y ayudando a identificar particiones, sectores, y otros datos estructurales del disco.

icat: sirve para extraer y mostrar el contenido de archivos individuales de una imagen de disco o un sistema de archivos

fls: sirve para listar los archivos y directorios de un sistema de archivos o una imagen de disco
## Referencias