## Objetivo
Let me in. Let me iiiiiiinnnnnnnnnnnnnnnnnnnn [http://mercury.picoctf.net:38322/](http://mercury.picoctf.net:38322)
## Solución
- Como la pagina no deja que entren si no es por PicoBrowse modificamos el Request  en Burpsuite cambiando el User-Agent por PicoBrowser para que nos deje acceder al sitio.
```http
GET / HTTP/1.1

Host: mercury.picoctf.net:38322

User-Agent: PicoBrowser

Gecko/20100101 Firefox/115.0

Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8

Accept-Language: en-US,en;q=0.5

Accept-Encoding: gzip, deflate, br

Connection: keep-alive

Upgrade-Insecure-Requests: 1




```
Ahora nos muestra un mensaje de que no confía en los que la visitan desde otro sitio por lo que agregamos un punto Referer para que la pagina vea que no hemos entrado desde otro sitio.
```bash
Referer: mercury.picoctf.net:38322
```
Ahora nos muestra un mensaje de que este sitio solo funciona en 2018 por lo que añadimos un encabezado de fecha para asegurarnos de que la solicitud se realiza en 2018.
```bash
Date: Wed, 31 Oct 2018 07:48:00 GMT
```
 Ahora nos muestra un mensaje de que no confía en los usuarios que pueden ser rastreados por lo que le añadimos el encabezado de solicitud DNT (Do Not Track) el cual indica la preferencia de seguimiento del usuario.
```bash
DNT: 1
```
 Ahora nos dice que la pagina es para personas de Suecia, así que trabajamos con otro encabezado X-Forward-For.
```bash
X-Forwarded-For: 102.177.146.1
```
Ahora dice que no hablamos sueco, por lo que tenemos que cambiar el encabezado de idioma a sueco.
```bash
Accept-Language: sv-sv,sv;q=0.5
```

La solicitud quedaría asi:
```http
GET / HTTP/1.1

Host: mercury.picoctf.net:38322

User-Agent: PicoBrowser

Date: Wed, 21 Oct 2018 07:28:00 GMT

DNT: 1

Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8

Accept-Language: sv-sv,sv;q=0.5

Accept-Encoding: gzip, deflate, br

Connection: keep-alive

X-Forwarded-For: 102.177.146.1

Referer: mercury.picoctf.net:38322

Upgrade-Insecure-Requests: 1
```


Y ya con esto obtenemos la bandera
```html
HTTP/1.1 200 OK

Content-Type: text/html; charset=utf-8

Content-Length: 1062



<!DOCTYPE html>
<html lang="en">

<head>
    <title>Who are you?</title>


    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css" rel="stylesheet">

    <link href="https://getbootstrap.com/docs/3.3/examples/jumbotron-narrow/jumbotron-narrow.css" rel="stylesheet">

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>

    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>


</head>

<body>

    <div class="container">
      <div class="jumbotron">
        <p class="lead"></p>
		<div class="row">
			<div class="col-xs-12 col-sm-12 col-md-12">
				<h3 style="color:green">What can I say except, you are welcome</h3>
			</div>
		</div>
		<br/>
		
			<b>picoCTF{http_h34d3rs_v3ry_c0Ol_much_w0w_b22d773c}</b>
		
	</div>
    <footer class="footer">
        <p>&copy; PicoCTF</p>
    </footer>

</div>
<script>
$(document).ready(function(){
    $(".close").click(function(){
        $("myAlert").alert("close");
    });
});
</script>
</body>

</html>
```

## Notas Adicionales
DNT - Permite a los usuarios indicar si prefieren la privacidad en lugar del contenido personalizado.
X-Forwarded-For - Se agrega automáticamente y lo ayuda a identificar la dirección IP de un cliente cuando usa un balanceador de carga HTTP o HTTPS.

## Referencias