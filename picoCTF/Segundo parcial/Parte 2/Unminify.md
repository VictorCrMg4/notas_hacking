## Objetivo
I don't like scrolling down to read the code of my website, so I've squished it. As a bonus, my pages load faster!Browse [here](http://titan.picoctf.net:/60946), and find the flag!
## Solución 1
Vemos el codigo de la pagina y vamos expandiendo cada seccion del código y ahi encontraremos la bandera.
```bash
<p class="picoCTF{pr3tty_c0d3_d9c45a0b}"></p>
```

## Solución 2
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ curl -s 'http://titan.picoctf.net:60946/' | grep picoCTF{
<!doctype html><html lang="en"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1"><title>picoCTF - picoGym | Unminify Challenge</title><link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png"><style>body{font-family:"Lucida Console",Monaco,monospace}h1,p{color:000}</style></head><body class="picoctf{}" style="margin:0"><div class="picoctf{}" style="margin:0;padding:0;background-color:#757575;display:auto;height:40%"><a class="picoctf{}" href="/"><img src="picoctf-logo-horizontal-white.svg" alt="picoCTF logo" style="display:inline-block;width:160px;height:90px;padding-left:30px"></a></div><center><br class="picoctf{}"><br class="picoctf{}"><div class="picoctf{}" style="padding-top:30px;border-radius:3%;box-shadow:0 5px 10px #0000004d;width:50%;align-self:center"><img class="picoctf{}" src="hero.svg" alt="flag art" style="width:150px;height:150px"><div class="picoctf{}" style="width:85%"><h2 class="picoctf{}">Welcome to my flag distribution website!</h2><div class="picoctf{}" style="width:70%"><p class="picoctf{}">If you're reading this, your browser has succesfully received the flag.</p><p class="picoCTF{pr3tty_c0d3_d9c45a0b}"></p><p class="picoctf{}">I just deliver flags, I don't know how to read them...</p></div></div><br class="picoctf{}"></div></center></body></html>

```

## Notas Adicionales
## Referencias