## Objetivo
Can you get the flag? Reverse engineer this [Python program](https://artifacts.picoctf.net/c/49/unpackme.flag.py).
## Solución
Revisamos el programa que nos dan.
```python
import base64
from cryptography.fernet import Fernet



payload = b'gAAAAABkzWGO_8MlYpNM0n0o718LL-w9m3rzXvCMRFghMRl6CSZwRD5DJOvN_jc8TFHmHmfiI8HWSu49MyoYKvb5mOGm_Jn4kkhC5fuRiGgmwEpxjh0z72dpi6TaPO2TorksAd2bNLemfTaYPf9qiTn_z9mvCQYV9cFKK9m1SqCSr4qDwHXgkQpm7IJAmtEJqyVUfteFLszyxv5-KXJin5BWf9aDPIskp4AztjsBH1_q9e5FIwIq48H7AaHmR8bdvjcW_ZrvhAIOInm1oM-8DjamKvhh7u3-lA=='

key_str = 'correctstaplecorrectstaplecorrec'
key_base64 = base64.b64encode(key_str.encode())
f = Fernet(key_base64)
plain = f.decrypt(payload)
exec(plain.decode())

```
- Podemos ver un `payload` (aparentemente codificado en base64), que será descifrado usando la variable `key_str`, que a su vez está codificada en base64.
- Después de esto, el `payload` decodificado será ejecutado, por lo que posiblemente, el `payload` en sí es un pequeño programa.
- Y esto lo podemos confirmar si intentamos ejecutar el programa.
```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte4]
└─$ python3 unpackme.flag.py 
What's the password? password
That password is incorrect.
                                
```
- Regresando al código si le hacemos una ligera modificación para imprimir la carga útil decodificada.
```python
import base64
from cryptography.fernet import Fernet



payload = b'gAAAAABkzWGO_8MlYpNM0n0o718LL-w9m3rzXvCMRFghMRl6CSZwRD5DJOvN_jc8TFHmHmfiI8HWSu49MyoYKvb5mOGm_Jn4kkhC5fuRiGgmwEpxjh0z72dpi6TaPO2TorksAd2bNLemfTaYPf9qiTn_z9mvCQYV9cFKK9m1SqCSr4qDwHXgkQpm7IJAmtEJqyVUfteFLszyxv5-KXJin5BWf9aDPIskp4AztjsBH1_q9e5FIwIq48H7AaHmR8bdvjcW_ZrvhAIOInm1oM-8DjamKvhh7u3-lA=='

key_str = 'correctstaplecorrectstaplecorrec'
key_base64 = base64.b64encode(key_str.encode())
f = Fernet(key_base64)
plain = f.decrypt(payload)
print(plain)
#exec(plain.decode())


```
- Tal como se esperaba, la carga útil es un script de Python, y nuestra bandera también se encuentra ahí para tomarla.
```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte4]
└─$ python3 unpackme.flag.py
b"\npw = input('What\\'s the password? ')\n\nif pw == 'batteryhorse':\n  print('picoCTF{175_chr157m45_5274ff21}')\nelse:\n  print('That password is incorrect.')\n\n"
        
```

## Notas Adicionales
## Referencias