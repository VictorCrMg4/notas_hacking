## Objetivo
Decrypt this [message](https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext).

## Solución
```bash
victormcm-picoctf@webshell:~$ nano cesar.py
```

```python
import string
import re
abc=string.ascii_letters

encriptado = open( 'ciphertext', 'r').read()
encriptado = re.findall('\{(.*?)\}', encriptado)[0]

rot= 22
salida= ''
for car in encriptado:
        salida += abc[(abc.find(car)+rot)%26]

print(salida)

```

```bash

victormcm-picoctf@webshell:~$ python cesar.py 
crossingtherubicondjneoach
```

## Notas Adicionales

## Referencias