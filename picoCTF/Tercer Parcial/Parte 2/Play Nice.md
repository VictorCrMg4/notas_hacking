## Objetivo
Not all ancient ciphers were so bad... The flag is not in standard format. `nc mercury.picoctf.net 19354` [playfair.py](https://mercury.picoctf.net/static/9ea1604c8767cd6545948ad54670c2bf/playfair.py)
## Solución
Nos dan un alfabeto y un mensaje encriptado.
```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte2]
└─$ nc mercury.picoctf.net 19354
Here is the alphabet: n5vgru7ehz1klja8s9340m2wcxbd6pqfitoy
Here is the encrypted message: hnjm2e4t51v16gsg104i4oi9wmrqli

```
Investigando descubrimos un tipo de cifrado llamado Fair play.

Entramos a esta pagina https://www.dcode.fr/chiffre-playfair buscamos la herramienta de Fair play cipher. Ahi dentro en el ingresamos nuestro mensaje y nuestro alfabeto.  


![[Pasted image 20241113130958.png]]

El resultado lo pasamos a minúsculas y lo introducimos como el texto plano que nos piden. 

```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte2]
└─$ python3                 
Python 3.12.6 (main, Sep  7 2024, 14:20:15) [GCC 14.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print("7V8441MFRERHDR8RH20F2FYA20NOAQ".lower())
7v8441mfrerhdr8rh20f2fya20noaq
>>> 
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte2]
└─$ nc mercury.picoctf.net 19354
Here is the alphabet: n5vgru7ehz1klja8s9340m2wcxbd6pqfitoy
Here is the encrypted message: hnjm2e4t51v16gsg104i4oi9wmrqli
What is the plaintext message? 7v8441mfrerhdr8rh20f2fya20noaq
Congratulations! Here's the flag: dbc8bf9bae7152d35d3c200c46a0fa30

```
## Notas Adicionales

## Referencias
https://en.wikipedia.org/wiki/Playfair_cipher