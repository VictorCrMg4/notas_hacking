## Objetivo
Caesar isn't the only guy who can create good ciphers, mine is more fancy.
## Solución
```bash
┌──(kali㉿kali)-[~/ctfAnuies]
└─$ cat fancy-cipher.py                               
from hidden import flag, shift

def encode(data, shift):
  enc = ''
  for _ in data:
    enc += chr((ord(_)+shift) % 0xff)
  return enc

assert code(flag, shift) == '-3(.4?B,5*9@7;065&0:&:6&-(5*@D'

```

Utilizamos este código para desencriptar
```python

encoded_message = '-3(.4?B,5*9@7;065&0:&:6&-(5*@D'

shift = (ord('D') - ord('}')) % 255

decoded_message = ''.join(chr((ord(char) - shift) % 0xff) for char in encoded_message)
print(f"Shift usado: {shift}")
print("Mensaje decodificado:", decoded_message)
------------------------------------
Shift usado: 198
Mensaje decodificado: flagmx{encryption_is_so_fancy}

```
## Notas Adicionales

## Referencias
