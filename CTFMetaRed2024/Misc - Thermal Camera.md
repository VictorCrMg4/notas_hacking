## Objetivo
Bank security personnel have intercepted a photograph taken with a thermal camera of a suspicious employee loitering near a safe. An investigation is underway to determine if this individual was able to obtain the code to the safe. Investigation of the safe's keypad reveals that it only accepts four-digit codes.

**Remember to use the flag format:

flagmx{XXXX}**
## Solución
- ##### Descargamos la imagen, y podemos apreciar que es un pad numérico, el cual se le pasó una cámara térmica para poder ver la contraseña de dicho pad.
```
┌──(kali㉿kali)-[~/MetaRedCTF]
└─$ open Thermal_camera.png
```

- ##### Nos guiaremos en que los puntos rojos que se vean menos grandes, son los primero números que se introdujeron, y los más grandes, los últimos... Guiándonos con eso, el formato del pad numérico es el siguiente:
```
1 2 3
4 5 6
7 8 9
- 0 -
```

![[Pasted image 20241015123309.png]]

- ##### Nos guiaremos por la opción de este pin:
```
0 - 5 - 7 - 3
```

- ##### Una vez descifrado el código del pad, lo introducimos al formato de la bandera y la obtenemos.
```
Flag: flagmx{0573}
```
## Notas Adicionales
- Una **cámara termográfica** (o **cámara térmica**) es un dispositivo que mide la temperatura y ofrece una imagen térmica de los objetos, sin necesidad de contacto, a partir de las emisiones de radiación infrarroja de estos.
#### Resuelto por: 
Miguel Ángel Juárez Martínez