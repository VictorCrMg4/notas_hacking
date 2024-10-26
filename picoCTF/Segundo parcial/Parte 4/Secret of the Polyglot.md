## Objetivo
The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/8/flag2of2-final.pdf).

## Solución
El Archivo es un pdf en la cual viene la segunda parte de la bandera
![[Pasted image 20241016232656.png]]
Nos damos cuenta que el pdf es también un archivo .png el revisar su codigo hexadecimal.
Lo cambiamos de nombre.

```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ mv flag2of2-final.pdf flag.png                  
                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ eog flag.png           
```

![[Pasted image 20241016232913.png]]
## Notas Adicionales

## Referencias
