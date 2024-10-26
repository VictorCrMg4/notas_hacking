## Objetivo
Download this packet capture and find the flag.

- [Download packet capture](https://artifacts.picoctf.net/c/133/capture.flag.pcap)
## Solución
- Abrimos el archivo con el wire shark.
```bash
──(kali㉿kali)-[~/picoCTF/eavesdrop]
└─$ file capture.flag.pcap 
capture.flag.pcap: pcap capture file, microsecond ts (little-endian) - version 2.4 (Ethernet, capture length 262144)
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/eavesdrop]
└─$ wireshark capture.flag.pcap&                              
[1] 3903
```
- Seleccionamos un archivo > Follow > TCP Steam; aquí nos muestra una conversación en donde le envía el comando para descomprimir el archivo y en que puerto se va a enviar el archivo.
```
Hey, how do you decrypt this file again?

You're serious?

Yeah, I'm serious

*sigh* openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123

Ok, great, thanks.

Let's use Discord next time, it's more secure.

C'mon, no one knows we use this program like this!

Whatever.

Hey.

Yeah?

Could you transfer the file to me again?

Oh great. Ok, over 9002?

Yeah, listening.

Sent it

Got it.

You're unbelievable
```
- Ahora filtramos la información para que nos de solo aquellos que se enviaron al puerto 9002 colocando el siguiente texto:
```bash
tcp.port == 9002
```
- De los archivos que nos filtro notamos que hay uno que es una contraseña salted las contraseñas es decir un open ssl archivo encriptado .

![[Pasted image 20241021224921.png]]

Cambiamos los datos a RAW en lugar de ASCII

![[Pasted image 20241021224805.png]]
Y lo exportamos como un archivo de nombre file.des3

Utilizamos el comando que venia en uno de los streams y la bandera aparecerá en un nuevo archivo file.txt.


```bash
┌──(kali㉿kali)-[~/picoCTF/eavesdrop]
└─$ openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/eavesdrop]
└─$ ls
capture.flag.pcap  file.des3  file.txt
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/eavesdrop]
└─$ cat file.txt                                      
picoCTF{nc_73115_411_5786acc3}        
```


## Notas Adicionales
## Referencias