## Objetivo
Try [here](http://titan.picoctf.net:50989/) to find the flag
## Solución
- Entramos al sitio web y contestamos el primer formulario y el segundo formulario, aquí abrimos la herramienta Burp Suit e interceptamos la petición del segundo formulario y cambiaremos el valor opt=0000 por:
```bash
opgt=0000
```
Una vez le damos foward en la pagina se mostrará el mensaje:
```bash
Welcome, admin you sucessfully bypassed the OTP request. Your Flag: picoCTF{#0TP_Bypvss_SuCc3$S_3e3ddc76}
```

## Notas Adicionales
## Referencias