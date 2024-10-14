## Objetivo
Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: [dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/626ea9c275fbd02dd3451b81f9c5e249/dds1-alpine.flag.img.gz)
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ gzip -d dds1-alpine.flag.img.gz 
                                                                                
┌──(kali㉿kali)-[~/picoCTF]
└─$ ls
base_images   dds1-alpine.flag.img  index.html  _rels
concat_v.png  docProps              ppt
                                                    
┌──(kali㉿kali)-[~/picoCTF]
└─$ srch_strings dds1-alpine.flag.img | grep picoCTF
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_a6f4cab5}

```
## Notas Adicionales
srch_strings: se usa para buscar y extraer cadenas de texto legibles dentro de archivos binarios.
## Referencias