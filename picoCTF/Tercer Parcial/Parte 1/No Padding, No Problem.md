## Objetivo
Oracles can be your best friend, they will decrypt anything, except the flag's ciphertext. How will you break it? Connect with `nc mercury.picoctf.net 28517`.
## Solución

```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte1]
└─$ nc mercury.picoctf.net 28517
Welcome to the Padding Oracle Challenge
This oracle will take anything you give it and decrypt using RSA. It will not accept the ciphertext with the secret message... Good Luck!


n: 94987845791958971610245684527526504076991217309070809953397476608667690041039503679778920129805256395601207996563836731828086267605258143358078279757279085959856689421047753770275677864809436725591320922794120518080674077013856118045296057140051631232323618343415419000276036021382719487296673019688495306181
e: 65537
ciphertext: 81690970645787341554968384871551134901218261908867970045795798669432912725273897965364844807878431292195666626852159083293818270768888184727424655660808681642333146404338730949867953541505747889964504948364275013807260907988834647985057123934662369570429973561814623427231186702043932757219121485359965717441


Give me ciphertext to decrypt: ^C

┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte1]
└─$ nano exp.py

```
- Creamos un programa en Python para que haga las operaciones y obtenga la bandera  automáticamente.
```python
from pwn import *
import binascii

r = remote('mercury.picoctf.net',28517)
r.recvlines(4)

r.recvuntil(b'n: ')
n = int(r.recvline().strip())

r.recvuntil(b'e: ')
e = int(r.recvline().strip())

r.recvuntil(b'ciphertext: ')
c = int(r.recvline().strip())

payload = c * pow(2,e,n)
r.sendlineafter(b'Give me ciphertext to decrypt: ', str(payload))

r.recvuntil(b'Here you go: ')
doubled_plain = int(r.recvline().strip())
print("Doubled Plain:", doubled_plain)

plain_hex = hex(doubled_plain // 2)[2:]
plain_bytes = bytes.fromhex(plain_hex)
print("Plain Text Hex:", plain_hex)
print("Plain Text:", plain_bytes.decode())

r.close()
```
- Ejecutamos el programa y obtendremos la bandera.
```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte1]
└─$ python3 exp.py  
[o] Opening connection to mercury.picoctf.net on port 28517: Trying 18.189.209.14[+] Opening connection to mercury.picoctf.net on port 28517: Done
/home/kali/picoCTF/tercerparcial/parte1/exp.py:17: BytesWarning: Text is not bytes; assuming ASCII, no guarantees. See https://docs.pwntools.com/#bytes
  r.sendlineafter(b'Give me ciphertext to decrypt: ', str(payload))
Doubled Plain: 580550060391700078946913236734911770139931497702556153513487440893406629034802718534645538074938502890769281669222390720762
Plain Text Hex: 7069636f4354467b6d347962335f54683073655f6d337335346733735f3472335f646966757272656e745f343030353533347d
Plain Text: picoCTF{m4yb3_Th0se_m3s54g3s_4r3_difurrent_4005534}
[*] Closed connection to mercury.picoctf.net port 28517

```

## Notas Adicionales
## Referencias
- [Homomorphic encryption](https://en.wikipedia.org/wiki/Homomorphic_encryption)