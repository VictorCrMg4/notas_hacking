## Objetivo
You will find the flag after analysing this apk Download [here](https://artifacts.picoctf.net/c/449/timer.apk).
## Solución
Un apk no es mas que un archivo zip

```bash
┌──(kali㉿kali)-[~/picoCTF/reversing2]
└─$ unzip timer.apk          
Archive:  timer.apk
  inflating: META-INF/com/android/build/gradle/app-metadata.properties  
  inflating: classes3.dex            
  inflating: classes2.dex            
  inflating: AndroidManifest.xml     
  inflating: res/anim/abc_fade_in.xml  
  inflating: res/anim/abc_fade_out.xml 
  ....
┌──(kali㉿kali)-[~/picoCTF/reversing2]
└─$ grep -R picoCTF                  
grep: classes3.dex: binary file matches
                                                                          
┌──(kali㉿kali)-[~/picoCTF/reversing2]
└─$ strings classes3.dex | grep pico
*picoCTF{t1m3r_r3v3rs3d_succ355fully_17496}
                  
```

## Forma 2
```bash
──(kali㉿kali)-[~/picoCTF/reversing2]
└─$ jadx-gui             
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
INFO  - output directory: classes3
INFO  - loading ...
INFO  - Loaded classes: 4, methods: 22, instructions: 575
INFO  - Resetting disk code cache, base dir: /home/kali/.cache/jadx/projects/classes3-bf75c3892fb30e52c67081b478e57cb9/code

```

![[Pasted image 20241030104613.png]]
## Notas Adicionales

## Referencias
