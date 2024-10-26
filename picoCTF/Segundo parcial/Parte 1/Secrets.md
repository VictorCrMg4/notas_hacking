## Objetivo
We have several pages hidden. Can you find the one with the flag?The website is running [here](http://saturn.picoctf.net:55045/).
## Solución
Entramos al codigo fuente
```html
|   |   |
|---|---|
||<!DOCTYPE html>|
||<html>|
||<head>|
||<title>Contact Us</title>|
||<!-- css -->|
||<link href="[secret/assets/index.css](http://saturn.picoctf.net:55045/secret/assets/index.css)" rel="stylesheet" />|
||</head>|
||<!-- ***** Header Area Start ***** -->|
||<div class="topnav">|
||<a href="[index.html](http://saturn.picoctf.net:55045/index.html)" >Home</a>|
||<a href="[about.html](http://saturn.picoctf.net:55045/about.html)" >About</a>|
||<a class="active" href="[contact.html](http://saturn.picoctf.net:55045/contact.html)">Contact</a>|
||</div>|
||<div class="deco"></div>|
||<div>|
||<h3>Lorem ipsum dolor sit amet, consectetur adipiscing elit</h3>|
||<p>|
||Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc diam urna,|
||viverra id sagittis vel, ultricies vel ante. Suspendisse tempus suscipit|
||sem ac blandit. Etiam et ex velit. Vestibulum nibh neque, placerat eget|
||sodales bibendum, pulvinar a libero. Proin turpis nisi, imperdiet ac|
||felis sed, posuere tincidunt enim. Maecenas in pretium velit, eu|
||consectetur erat. Aliquam viverra laoreet laoreet. Phasellus sapien|
||ipsum, euismod pellentesque tincidunt eu, euismod vitae lectus. Nulla in|
||sem velit. Aliquam ut nisi molestie, auctor nulla at, tempus leo. Nulla|
||id nisl convallis, bibendum urna eu, fringilla turpis. Nam sodales erat|
||vel sapien fermentum scelerisque. Vivamus iaculis nisl at eros aliquam,|
||a pulvinar magna placerat. Sed eu commodo sapien. Aliquam tristique|
||dapibus urna, in blandit lacus volutpat vel.|
||</p>|
||</div>|
||<div>|
||<h3>Lorem ipsum dolor sit amet, consectetur adipiscing elit</h3>|
||<p>|
||Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc diam urna,|
||viverra id sagittis vel, ultricies vel ante. Suspendisse tempus suscipit|
||sem ac blandit. Etiam et ex velit. Vestibulum nibh neque, placerat eget|
||sodales bibendum, pulvinar a libero. Proin turpis nisi, imperdiet ac|
||felis sed, posuere tincidunt enim. Maecenas in pretium velit, eu|
||consectetur erat. Aliquam viverra laoreet laoreet. Phasellus sapien|
||ipsum, euismod pellentesque tincidunt eu, euismod vitae lectus. Nulla in|
||sem velit. Aliquam ut nisi molestie, auctor nulla at, tempus leo. Nulla|
||id nisl convallis, bibendum urna eu, fringilla turpis. Nam sodales erat|
||vel sapien fermentum scelerisque. Vivamus iaculis nisl at eros aliquam,|
||a pulvinar magna placerat. Sed eu commodo sapien. Aliquam tristique|
||dapibus urna, in blandit lacus volutpat vel.|
||</p>|
||</div>|
||<div>|
||<h3>Lorem ipsum dolor sit amet, consectetur adipiscing elit</h3>|
||<p>|
||Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc diam urna,|
||viverra id sagittis vel, ultricies vel ante. Suspendisse tempus suscipit|
||sem ac blandit. Etiam et ex velit. Vestibulum nibh neque, placerat eget|
||sodales bibendum, pulvinar a libero. Proin turpis nisi, imperdiet ac|
||felis sed, posuere tincidunt enim. Maecenas in pretium velit, eu|
||consectetur erat. Aliquam viverra laoreet laoreet. Phasellus sapien|
||ipsum, euismod pellentesque tincidunt eu, euismod vitae lectus. Nulla in|
||sem velit. Aliquam ut nisi molestie, auctor nulla at, tempus leo. Nulla|
||id nisl convallis, bibendum urna eu, fringilla turpis. Nam sodales erat|
||vel sapien fermentum scelerisque. Vivamus iaculis nisl at eros aliquam,|
||a pulvinar magna placerat. Sed eu commodo sapien. Aliquam tristique|
||dapibus urna, in blandit lacus volutpat vel.|
||</p>|
||</div><div>|
||<h3>Lorem ipsum dolor sit amet, consectetur adipiscing elit</h3>|
||<p>|
||Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc diam urna,|
||viverra id sagittis vel, ultricies vel ante. Suspendisse tempus suscipit|
||sem ac blandit. Etiam et ex velit. Vestibulum nibh neque, placerat eget|
||sodales bibendum, pulvinar a libero. Proin turpis nisi, imperdiet ac|
||felis sed, posuere tincidunt enim. Maecenas in pretium velit, eu|
||consectetur erat. Aliquam viverra laoreet laoreet. Phasellus sapien|
||ipsum, euismod pellentesque tincidunt eu, euismod vitae lectus. Nulla in|
||sem velit. Aliquam ut nisi molestie, auctor nulla at, tempus leo. Nulla|
||id nisl convallis, bibendum urna eu, fringilla turpis. Nam sodales erat|
||vel sapien fermentum scelerisque. Vivamus iaculis nisl at eros aliquam,|
||a pulvinar magna placerat. Sed eu commodo sapien. Aliquam tristique|
||dapibus urna, in blandit lacus volutpat vel.|
||</p>|
||</div>|
||<div>|
||<h3>Lorem ipsum dolor sit amet, consectetur adipiscing elit</h3>|
||<p>|
||Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc diam urna,|
||viverra id sagittis vel, ultricies vel ante. Suspendisse tempus suscipit|
||sem ac blandit. Etiam et ex velit. Vestibulum nibh neque, placerat eget|
||sodales bibendum, pulvinar a libero. Proin turpis nisi, imperdiet ac|
||felis sed, posuere tincidunt enim. Maecenas in pretium velit, eu|
||consectetur erat. Aliquam viverra laoreet laoreet. Phasellus sapien|
||ipsum, euismod pellentesque tincidunt eu, euismod vitae lectus. Nulla in|
||sem velit. Aliquam ut nisi molestie, auctor nulla at, tempus leo. Nulla|
||id nisl convallis, bibendum urna eu, fringilla turpis. Nam sodales erat|
||vel sapien fermentum scelerisque. Vivamus iaculis nisl at eros aliquam,|
||a pulvinar magna placerat. Sed eu commodo sapien. Aliquam tristique|
||dapibus urna, in blandit lacus volutpat vel.|
||</p>|
||</div>|
||<div>|
||<h3>Lorem ipsum dolor sit amet, consectetur adipiscing elit</h3>|
||<p>|
||Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc diam urna,|
||viverra id sagittis vel, ultricies vel ante. Suspendisse tempus suscipit|
||sem ac blandit. Etiam et ex velit. Vestibulum nibh neque, placerat eget|
||sodales bibendum, pulvinar a libero. Proin turpis nisi, imperdiet ac|
||felis sed, posuere tincidunt enim. Maecenas in pretium velit, eu|
||consectetur erat. Aliquam viverra laoreet laoreet. Phasellus sapien|
||ipsum, euismod pellentesque tincidunt eu, euismod vitae lectus. Nulla in|
||sem velit. Aliquam ut nisi molestie, auctor nulla at, tempus leo. Nulla|
||id nisl convallis, bibendum urna eu, fringilla turpis. Nam sodales erat|
||vel sapien fermentum scelerisque. Vivamus iaculis nisl at eros aliquam,|
||a pulvinar magna placerat. Sed eu commodo sapien. Aliquam tristique|
||dapibus urna, in blandit lacus volutpat vel.|
||</p>|
||</div>|
||</body>|
||</html>|
|||
```
Exploramos la carpeta http://saturn.picoctf.net:55045/secret/
```html
|   |   |
|---|---|
||<!DOCTYPE html>|
||<html>|
||<head>|
||<title></title>|
||<link rel="stylesheet" href="[hidden/file.css](http://saturn.picoctf.net:55045/secret/hidden/file.css)" />|
||</head>|
|||
||<body>|
||<h1>Finally. You almost found me. you are doing well</h1>|
||<img src="[https://media1.tenor.com/images/0a6aff9f825af62c05adfbd75039cc7b/tenor.gif?itemid=4648337](https://media1.tenor.com/images/0a6aff9f825af62c05adfbd75039cc7b/tenor.gif?itemid=4648337)" alt="Something Like That GIF - Andy Parksandrecreation Wtf GIFs" style="max-width: 833px; background-color: rgb(151, 121, 85);" width="833" height="937.125">|
||</body>|
||</html>|
|||
```
Entramos a la carpeta view-source:http://saturn.picoctf.net:55045/secret/hidden/

```html
|   |   |
|---|---|
||<!DOCTYPE html>|
||<html>|
||<head>|
||<title>LOGIN</title>|
||<!-- css -->|
||<link href="[superhidden/login.css](http://saturn.picoctf.net:55045/secret/hidden/superhidden/login.css)" rel="stylesheet" />|
||</head>|
||<body>|
||<form>|
||<div class="container">|
||<form method="" action="/secret/assets/popup.js">|
||<div class="row">|
||<h2 style="text-align: center">|
||Login with Social Media or Manually|
||</h2>|
||<div class="vl">|
||<span class="vl-innertext">or</span>|
||</div>|
|||
||<div class="col">|
||<a href="[#](http://saturn.picoctf.net:55045/secret/hidden/#)" class="fb btn">|
||<i class="fa fa-facebook fa-fw"></i> Login with Facebook|
||</a>|
||<a href="[#](http://saturn.picoctf.net:55045/secret/hidden/#)" class="twitter btn">|
||<i class="fa fa-twitter fa-fw"></i> Login with Twitter|
||</a>|
||<a href="[#](http://saturn.picoctf.net:55045/secret/hidden/#)" class="google btn">|
||<i class="fa fa-google fa-fw"></i> Login with Google+|
||</a>|
||</div>|
|||
||<div class="col">|
||<div class="hide-md-lg">|
||<p>Or sign in manually:</p>|
||</div>|
|||
||<input|
||type="text"|
||name="username"|
||placeholder="Username"|
||required|
||/>|
||<input|
||type="password"|
||name="password"|
||placeholder="Password"|
||required|
||/>|
||<input type="hidden" name="db" value="superhidden/xdfgwd.html" />|
|||
||<input|
||type="submit"|
||value="Login"|
||onclick="alert('Thank you for the attempt but oops! try harder. better luck next time')"|
||/>|
||</div>|
||</div>|
||</form>|
||</div>|
|||
||<div class="bottom-container">|
||<div class="row">|
||<div class="col">|
||<a href="[#](http://saturn.picoctf.net:55045/secret/hidden/#)" style="color: white" class="btn">Sign up</a>|
||</div>|
||<div class="col">|
||<a href="[#](http://saturn.picoctf.net:55045/secret/hidden/#)" style="color: white" class="btn">Forgot password?</a>|
||</div>|
||</div>|
||</div>|
||</form>|
||</body>|
||</html>|
|||

```

Finalmente entramos a la carpeta
http://saturn.picoctf.net:55045/secret/hidden/superhidden/

```html
|<!DOCTYPE html>|
||<html>|
||<head>|
||<title></title>|
||<link rel="stylesheet" href="[mycss.css](http://saturn.picoctf.net:55045/secret/hidden/superhidden/mycss.css)" />|
||</head>|
|||
||<body>|
||<h1>Finally. You found me. But can you see me</h1>|
||<h3 class="flag">picoCTF{succ3ss_@h3n1c@10n_790d2615}</h3>|
||</body>|
||</html>|
||
```

## Notas Adicionales

## Referencias
