
## Objetivo
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/b6205dd933ec01c022c4e6acbdf11116/dolls.jpg)
## Solución
```bash                                                               ┌──(kali㉿kali)-[~/picoCTF]
└─$ unzip dolls.jpg 
Archive:  dolls.jpg
warning [dolls.jpg]:  272492 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: base_images/2_c.jpg     
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF]
└─$ ls
base_images  dolls.jpg
                                                                                                                                                                
┌──(kali㉿kali)-[~/picoCTF]
└─$ cd base_images                                                                                                                                                                 
┌──(kali㉿kali)-[~/picoCTF/base_images]
└─$ unzip 2_c.jpg  
Archive:  2_c.jpg
warning [2_c.jpg]:  187707 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: base_images/3_c.jpg     
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/base_images]
└─$ ls            
2_c.jpg  base_images
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/base_images]
└─$ cd base_images 
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/base_images/base_images]
└─$ unzip 3_c.jpg 
Archive:  3_c.jpg
warning [3_c.jpg]:  123606 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: base_images/4_c.jpg     
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/base_images/base_images]
└─$ cd base_images 
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/base_images/base_images/base_images]
└─$ unzip 4_c.jpg 
Archive:  4_c.jpg
warning [4_c.jpg]:  79578 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: flag.txt                
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/base_images/base_images/base_images]
└─$ ls
4_c.jpg  flag.txt
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/base_images/base_images/base_images]
└─$ cat flag.txt  
picoCTF{4f11048e83ffc7d342a15bd2309b47de}               
```

## Notas Adicionales

## Referencias
