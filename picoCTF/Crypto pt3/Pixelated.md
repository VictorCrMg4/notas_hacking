## Objetivo
I have these 2 images, can you make a flag out of them? [scrambled1.png](https://mercury.picoctf.net/static/6e4afb967ef8c865f79f3a8cd7767cca/scrambled1.png) [scrambled2.png](https://mercury.picoctf.net/static/6e4afb967ef8c865f79f3a8cd7767cca/scrambled2.png)
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF/crypto]
└─$ java -jar /opt/stegsolve.jar    
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true

```

Combinar las dos imagenes y sumar los pixeles
Analyse >Image Combiner
	
![[Pasted image 20241023105906.png]]

## Solucion 2
```bash
┌──(kali㉿kali)-[~/picoCTF/crypto]
└─$ convert scrambled1.png scrambled2.png -compose Add -composite bandera.png 

```

## Solucion 3
```python
from PIL import Image
import numpy as np
imagen1 = np.asarray(Image.open('scrambled1.png'))
imagen2 = np.asarray(Image.open('scrambled2.png'))

#print(imagen1)
todo= imagen2 + imagen1

nuevaimagen = Image.fromarray(todo)
nuevaimagen.save('lachida.png')
```
## Notas Adicionales

## Referencias
