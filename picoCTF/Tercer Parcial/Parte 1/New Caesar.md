## Objetivo
We found a brand new type of encryption, can you break the secret code? (Wrap with picoCTF{}) `ihjghbjgjhfbhbfcfjflfjiifdfgffihfeigidfligigffihfjfhfhfhigfjfffjfeihihfdieieih` [new_caesar.py](https://mercury.picoctf.net/static/2fc43dd1a3718df7debf367b0e092831/new_caesar.py)
## Soluciónc
- Revisamos el código que encripto la bandera.
```python
import string

LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

def b16_encode(plain):
        enc = ""
        for c in plain:
                binary = "{0:08b}".format(ord(c))
                enc += ALPHABET[int(binary[:4], 2)]
                enc += ALPHABET[int(binary[4:], 2)]
        return enc

def shift(c, k):
        t1 = ord(c) - LOWERCASE_OFFSET
        t2 = ord(k) - LOWERCASE_OFFSET
        return ALPHABET[(t1 + t2) % len(ALPHABET)]

flag = "redacted"
key = "redacted"
assert all([k in ALPHABET for k in key])
assert len(key) == 1

b16 = b16_encode(flag)
enc = ""
for i, c in enumerate(b16):
        enc += shift(c, key[i % len(key)])
print(enc)

```
- Creamos un programa en Python que desencripté el texto que nos dieron.
```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte1]
└─$ nano solve.py

```
```python
import string

LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

def b16_decode(cipher):
    dec = ""
    for c in range(0, len(cipher), 2):
        b = ""
        b += "{0:04b}".format(ALPHABET.index(cipher[c]))
        b += "{0:04b}".format(ALPHABET.index(cipher[c + 1]))
        dec += chr(int(b, 2))
    return dec

def unshift(c, k):
    t1 = ord(c) - LOWERCASE_OFFSET
    t2 = ord(k) - LOWERCASE_OFFSET
    return ALPHABET[(t1 - t2) % len(ALPHABET)]

enc = "ihjghbjgjhfbhbfcfjflfjiifdfgffihfeigidfligigffihfjfhfhfhigfjfffjfeihihfdieieih"

for key in ALPHABET:
    s = ""
    for i, c in enumerate(enc):
        s += unshift(c, key[i % len(key)])
    s = b16_decode(s)
    print(s)
```
- Ejecutamos el programa.
```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte1]
└─$ python3 solve.py 
qQqRY[YSVUT[UYWWWYUYTS
v`@`AHJHwBEDvCurJuuDvHFFFuHDHCvvBssv
et_tu?_0797f143e2da9dd3e7555d7372ee1bbe
TcNcd.N/&(&U #"T!SP(SS"T&$$$S&"&!TT QQT
CR=RS=DCBOBBCBCC@@C
2A,AB
321>112122??2
!01ûóõó"ýðÿ!þ -õ  ÿ!óñññ óÿóþ!!ý..!
/
/ ê
ëâäâìïîíäîâàààâîâíì
ùÙùÚÑÓÑÛÞÝÜ
           ÓÝÑßßßÑÝÑÜÛ


ÈèÉÀÂÀÿÊÍÌþËýúÂýýÌþÀÎÎÎýÀÌÀËþþÊûûþ
íü×üý·×¸¿±¿î¹¼»íºìé±ìì»í¿½½½ì¿»¿ºíí¹êêí
ÜëÆëì¦Æ§® ®Ý¨«ªÜ©ÛØ ÛÛªÜ®¬¬¬Û®ª®©ÜÜ¨ÙÙÜ
ËÚµÚÛµÌËÊÇÊÊËËËÈÈË
ºÉ¤ÉÊ¤»º¹¶¹¹º¹ºº··º
©¸¸¹st{}{ªuxw©v¨¥}¨¨w©{yyy¨{w{v©©u¦¦©
§§¨bcjljdgfelfjhhhjfjed

```
- Buscamos el texto y le aplicamos el formato de la bandera.
```bash
picoCTF{et_tu?_0797f143e2da9dd3e7555d7372ee1bbe}
```

## Notas Adicionales
## Referencias