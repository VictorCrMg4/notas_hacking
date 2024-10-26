## Objetivo
Someone might have hidden the password in the trace file. Find the key to unlock [this file](https://artifacts.picoctf.net/c/493/flag.zip). [This tracefile](https://artifacts.picoctf.net/c/493/dump.pcap) might be good to analyze.
## Solución

```bash
┌──(kali㉿kali)-[~/picoCTF/findnopen]
└─$ ls
dump.pcap  flag.zip

```
-  AL tratar de descomprimir el archivo zip nos pide una contraseña
- Abrimos el archivo pcap con wireshark.
```bash
┌──(kali㉿kali)-[~/picoCTF/findnopen]
└─$ unzip flag.zip
Archive:  flag.zip
[flag.zip] flag password: 

┌──(kali㉿kali)-[~/picoCTF/findnopen]
└─$ wireshark dump.pcap &                             
[1] 24886
            
```
- Una vez dentro observamos que hay varios archivos que tienen un protocolo diferente al de MDNS por lo que los filtramos.
```bash
!mdns
```
- Al explorar los archivos nos damos cuenta que en realidad son solo 5 archivos diferentes pero uno de ellos parece estar codificada en base64 por lo que la decodificamos.
```bash
                                                                     
┌──(kali㉿kali)-[~/picoCTF/findnopen]
└─$ echo -n aaAABBHHPJGTFRLKVGhpcyBpcyB0aGUgc2VjcmV0OiBwaWNvQ1RGe1IzNERJTkdfTE9LZF8= | base64 -di
i��<���This is the secret: picoCTF{R34DING_LOKd_   
```
- Y lo que nos da es la contraseña para poder descomprimir el paquete zip por lo que procedemos a descomprimirlo y mostramos el contenido del archivo que descomprimimos.
```bash
┌──(kali㉿kali)-[~/picoCTF/findnopen]
└─$ unzip flag.zip
Archive:  flag.zip
[flag.zip] flag password: 
 extracting: flag                    
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/findnopen]
└─$ cat flag
picoCTF{R34DING_LOKd_fil56_succ3ss_419835ef}
                                       
```


## Notas Adicionales
## Referencias