## Objetivo
Now for something a little different. `0x2262c96b` is loaded into memory in the `main` function. Examine byte-wise the memory that the constant is loaded in by using the GDB command `x/4xb addr`. The flag is the four bytes as they are stored in memory. If you find the bytes `0x11 0x22 0x33 0x44` in the memory location, your flag would be: `picoCTF{0x11223344}`.Debug [this](https://artifacts.picoctf.net/c/531/debugger0_c).
## Solución

```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte4]
└─$ chmod +x debugger0_b 
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte4]
└─$ wget https://artifacts.picoctf.net/c/531/debugger0_c
--2024-11-17 18:59:44--  https://artifacts.picoctf.net/c/531/debugger0_c
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.26, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16304 (16K) [application/octet-stream]
Saving to: ‘debugger0_c’

debugger0_c          100%[===================>]  15.92K  --.-KB/s    in 0.003s  

2024-11-17 18:59:50 (5.13 MB/s) - ‘debugger0_c’ saved [16304/16304]

                                                                                 
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte4]
└─$ chmod +x debugger0_c            
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte4]
└─$ gdb -q debugger0_c
Reading symbols from debugger0_c...
(No debugging symbols found in debugger0_c)
(gdb) set disassembly-flavor intel 
(gdb)  info functions 
All defined functions:

Non-debugging symbols:
0x0000000000401000  _init
0x0000000000401020  _start
0x0000000000401050  _dl_relocate_static_pie
0x0000000000401060  deregister_tm_clones
0x0000000000401090  register_tm_clones
0x00000000004010d0  __do_global_dtors_aux
0x0000000000401100  frame_dummy
0x0000000000401106  main
0x0000000000401130  __libc_csu_init
0x00000000004011a0  __libc_csu_fini
0x00000000004011a8  _fini
(gdb) disassemble main 
Dump of assembler code for function main:
   0x0000000000401106 <+0>:     endbr64
   0x000000000040110a <+4>:     push   rbp
   0x000000000040110b <+5>:     mov    rbp,rsp
   0x000000000040110e <+8>:     mov    DWORD PTR [rbp-0x14],edi
   0x0000000000401111 <+11>:    mov    QWORD PTR [rbp-0x20],rsi
   0x0000000000401115 <+15>:    mov    DWORD PTR [rbp-0x4],0x2262c96b
   0x000000000040111c <+22>:    mov    eax,DWORD PTR [rbp-0x4]
   0x000000000040111f <+25>:    pop    rbp
   0x0000000000401120 <+26>:    ret
End of assembler dump.
(gdb) 

```
- Creamos un `breakpoint` al principio del `main` para que se detenga la ejecución del programa.
```bash
End of assembler dump.
(gdb) break main
Breakpoint 1 at 0x40110e
(gdb) r
Starting program: /home/kali/picoCTF/tercerparcial/parte4/debugger0_c 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, 0x000000000040110e in main ()
(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000401106 <+0>:     endbr64
   0x000000000040110a <+4>:     push   rbp
   0x000000000040110b <+5>:     mov    rbp,rsp
=> 0x000000000040110e <+8>:     mov    DWORD PTR [rbp-0x14],edi
   0x0000000000401111 <+11>:    mov    QWORD PTR [rbp-0x20],rsi
   0x0000000000401115 <+15>:    mov    DWORD PTR [rbp-0x4],0x2262c96b
   0x000000000040111c <+22>:    mov    eax,DWORD PTR [rbp-0x4]
   0x000000000040111f <+25>:    pop    rbp
   0x0000000000401120 <+26>:    ret
End of assembler dump.

```
- Creamos otro `breakpoint` en la línea 25 para que se detenga la ejecución del programa.
```bash
(gdb) break *(main+25)
Breakpoint 2 at 0x40111f
(gdb) continue
Continuing.

Breakpoint 2, 0x000000000040111f in main ()
(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000401106 <+0>:     endbr64
   0x000000000040110a <+4>:     push   rbp
   0x000000000040110b <+5>:     mov    rbp,rsp
   0x000000000040110e <+8>:     mov    DWORD PTR [rbp-0x14],edi
   0x0000000000401111 <+11>:    mov    QWORD PTR [rbp-0x20],rsi
   0x0000000000401115 <+15>:    mov    DWORD PTR [rbp-0x4],0x2262c96b
   0x000000000040111c <+22>:    mov    eax,DWORD PTR [rbp-0x4]
=> 0x000000000040111f <+25>:    pop    rbp
   0x0000000000401120 <+26>:    ret
End of assembler dump.

```
- Inspeccionamos el contenido del registro EAX en este punto ejecutando.
```bash
(gdb) info registers eax
eax            0x2262c96b          576899435
(gdb) 

```
- Sin embargo, esta no es nuestra bandera. El comando `file` indica el uso de una representación `little-endian`, lo que implica el almacenamiento de los bytes en orden inverso. Siguiendo la sugerencia del reto, inspeccionamos el contenido real de la memoria.
```bash
(gdb) x/4xb $rbp-4
0x7fffffffdcfc: 0x6b    0xc9    0x62    0x22
(gdb) c
Continuing.
[Inferior 1 (process 27814) exited with code 0153]
(gdb) quit

```
- Y ya obtenemos la bandera en el formato requerido por el reto.
```bash
picoCTF{0x6bc96222}
```

## Notas Adicionales
## Referencias