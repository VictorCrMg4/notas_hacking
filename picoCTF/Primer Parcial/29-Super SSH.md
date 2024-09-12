## Objetivo
Using a Secure Shell (SSH) is going to be pretty important.Can you `ssh` as `ctf-player` to `titan.picoctf.net` at port `57536` to get the flag?You'll also need the password `1db87a14`. If asked, accept the fingerprint with `yes`.If your device doesn't have a shell, you can use: [https://webshell.picoctf.org](https://webshell.picoctf.org/)If you're not sure what a shell is, check out our Primer: [https://primer.picoctf.com/#the_shell](https://primer.picoctf.com/#_the_shell)
## Solución
```bash
victormcm-picoctf@webshell:~$ ssh ctf-player@titan.picoctf.net -p57536
ctf-player@titan.picoctf.net's password: 
Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_45a48857}
Connection to titan.picoctf.net closed.
```
## Notas Adicionales

## Referencias