## Objetivo
[🥛](http://mercury.picoctf.net:5013/)
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ exiftool concat_v.png
ExifTool Version Number         : 12.76
File Name                       : concat_v.png
Directory                       : .
File Size                       : 18 MB
File Modification Date/Time     : 2021:03:15 14:24:47-04:00
File Access Date/Time           : 2024:10:14 14:59:09-04:00
File Inode Change Date/Time     : 2024:10:14 14:57:52-04:00
File Permissions                : -rw-rw-r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 1280
Image Height                    : 47520
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 1280x47520
Megapixels                      : 60.8
┌──(kali㉿kali)-[~/picoCTF]
└─$ export RUBY_THREAD_VM_STACK_SIZE=500000000
                                                                                 
┌──(kali㉿kali)-[~/picoCTF]
└─$ zsteg -a concat_v.png | grep pico         
b1,b,lsb,xy         .. text: "picoCTF{imag3_m4n1pul4t10n_sl4p5}\n"
/var/lib/gems/3.1.0/gems/iostruct-0.1.3/lib/iostruct.rb:159:in `inspect': stack level too deep (SystemStackError)
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.1.0/gems/iostruct-0.1.3/lib/iostruct.rb:159:in `inspect'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.1.0/gems/iostruct-0.1.3/lib/iostruct.rb:159:in `inspect'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.1.0/gems/iostruct-0.1.3/lib/iostruct.rb:159:in `inspect'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.1.0/gems/iostruct-0.1.3/lib/iostruct.rb:159:in `inspect'
         ... 4807703 levels...
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg.rb:26:in `run'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/bin/zsteg:8:in `<top (required)>'
        from /usr/local/bin/zsteg:25:in `load'
        from /usr/local/bin/zsteg:25:i                  
```
## Notas Adicionales
zsteg: Saca infromacion de imagenes que tiene esteganografia
## Referencias