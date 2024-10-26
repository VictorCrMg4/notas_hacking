## Objetivo
My dog-sitter's brother made this website but I can't get in; can you help?[login.mars.picoctf.net](https://login.mars.picoctf.net/)
## Solución
Entramos al codigo fuente de la página  y revisamos el archivo index.js
```bash
<script src="index.js"></script>
```
Aparece la validacion del usuario y contraseña mas ahí mismo viene la bandera codifica en base64
```
(async()=>{await new Promise((e=>window.addEventListener("load",e))),document.querySelector("form").addEventListener("submit",(e=>{e.preventDefault();const r={u:"input[name=username]",p:"input[name=password]"},t={};for(const e in r)t[e]=btoa(document.querySelector(r[e]).value).replace(/=/g,"");return"YWRtaW4"!==t.u?alert("Incorrect Username"):"cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ"!==t.p?alert("Incorrect Password"):void alert(`Correct Password! Your flag is ${atob(t.p)}.`)}))})();
```

En cyber chef decodificamos la bandera
```bash
Texto codificado: "cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ"
Texto decodificado: picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}
```

## Notas Adicionales
## Referencias
https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=Y0dsamIwTlVSbnMxTTNKMk0zSmZOVE55ZGpOeVh6VXpjbll6Y2w4MU0zSjJNM0pmTlROeWRqTnlmUQ&oenc=65001