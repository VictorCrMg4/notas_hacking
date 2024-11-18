## Objetivo
Can you get the flag? Reverse engineer this [binary](https://artifacts.picoctf.net/c/205/unpackme-upx).
## Solución

```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte4]
└─$ file unpackme-upx     
unpackme-upx: ELF 64-bit LSB executable, x86-64, version 1 (GNU/Linux), statically linked, no section header
```
- Descomprimimos el archivo que nos dieron, despues abrimos el binario con la herramienta de `ghidra`.
```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte4]
└─$ upx -d unpackme-upx      
                       Ultimate Packer for eXecutables
                          Copyright (C) 1996 - 2024
UPX 4.2.4       Markus Oberhumer, Laszlo Molnar & John Reiser    May 9th 2024

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
   1006445 <-    379188   37.68%   linux/amd64   unpackme-upx

Unpacked 1 file.


┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte4]
└─$ ghidra         
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
```
- Una vez abierto el programa buscamos la función del `main`.
```c

undefined8 main(void)

{
  long in_FS_OFFSET;
  int local_44;
  char *local_40;
  undefined8 local_38;
  undefined8 local_30;
  undefined8 local_28;
  undefined4 local_20;
  undefined2 local_1c;
  long local_10;
  
  local_10 = *(long *)(in_FS_OFFSET + 0x28);
  local_38 = 0x4c75257240343a41;
  local_30 = 0x30623e306b6d4146;
  local_28 = 0x6865666430486637;
  local_20 = 0x36636433;
  local_1c = 0x4e;
  printf("What\'s my favorite number? ");
  __isoc99_scanf(&DAT_004b3020,&local_44);
  if (local_44 == 0xb83cb) {
    local_40 = (char *)rotate_encrypt(0,&local_38);
    fputs(local_40,(FILE *)stdout);
    putchar(10);
    free(local_40);
  }
  else {
    puts("Sorry, that\'s not it!");
  }
  if (local_10 != *(long *)(in_FS_OFFSET + 0x28)) {
                    /* WARNING: Subroutine does not return */
    __stack_chk_fail();
  }
  return 0;
}


```
- Notamos que si el `local_44` es igual al valor `0xb83cb` (`754635`)nos dará  la bandera, por lo que ejecutamos el programa y le enviamos el valor solicitado.
```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte4]
└─$ chmod +x unpackme-upx 
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte4]
└─$ ./unpackme-upx 
What's my favorite number? 754635
picoCTF{up><_m3_f7w_5769b54e}


```

## Notas Adicionales
## Referencias
- [UPX](https://en.wikipedia.org/wiki/UPX)