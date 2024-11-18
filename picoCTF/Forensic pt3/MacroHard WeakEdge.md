## Objetivo
I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/2e739f9e0dc9f4c1556ea6b033c3ec8e/Forensics%20is%20fun.pptm)
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ unzip Forensics\ is\ fun.pptm
Archive:  Forensics is fun.pptm
  inflating: [Content_Types].xml     
  inflating: _rels/.rels             
  inflating: ppt/presentation.xml    
  inflating: ppt/slides/_rels/slide46.xml.rels  
  inflating: ppt/slides/slide1.xml   
  inflating: ppt/slides/slide2.xml   
  inflating: ppt/slides/slide3.xml   
  inflating: ppt/slides/slide4.xml   
  inflating: ppt/slides/slide5.xml   
  inflating: ppt/slides/slide6.xml   
  inflating: ppt/slides/slide7.xml   
  inflating: ppt/slides/slide8.xml   
  inflating: ppt/slides/slide9.xml   
  ....
  inflating: ppt/theme/theme1.xml    
 extracting: docProps/thumbnail.jpeg  
  inflating: ppt/vbaProject.bin      
  inflating: ppt/presProps.xml       
  inflating: ppt/viewProps.xml       
  inflating: ppt/tableStyles.xml     
  inflating: docProps/core.xml       
  inflating: docProps/app.xml        
  inflating: ppt/slideMasters/hidden  
┌──(kali㉿kali)-[~/picoCTF]
└─$ cd ppt/slideMasters/   
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/ppt/slideMasters]
└─$ cat hidden          
Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q                                                                                 
┌──(kali㉿kali)-[~/picoCTF/ppt/slideMasters]
└─$ cat hidden | tr -d ' ' | base64 -d
cd flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}base64: invalid input

  
```
## Notas Adicionales
tr - d ' ' elimina los espacios
## Referencias
