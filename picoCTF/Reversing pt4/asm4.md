## Objetivo
What will asm4("picoCTF_f97bb") return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://jupiter.challenges.picoctf.org/static/76ef117df9226a8a9306a8865b14068e/test.S)
## Solución
Nos dan este codigo en lenguaje ensamblador.

```asm
asm4:
        <+0>:   push   ebp
        <+1>:   mov    ebp,esp
        <+3>:   push   ebx
        <+4>:   sub    esp,0x10
        <+7>:   mov    DWORD PTR [ebp-0x10],0x27a
        <+14>:  mov    DWORD PTR [ebp-0xc],0x0
        <+21>:  jmp    0x518 <asm4+27>
        <+23>:  add    DWORD PTR [ebp-0xc],0x1
        <+27>:  mov    edx,DWORD PTR [ebp-0xc]
        <+30>:  mov    eax,DWORD PTR [ebp+0x8]
        <+33>:  add    eax,edx
        <+35>:  movzx  eax,BYTE PTR [eax]
        <+38>:  test   al,al
        <+40>:  jne    0x514 <asm4+23>
        <+42>:  mov    DWORD PTR [ebp-0x8],0x1
        <+49>:  jmp    0x587 <asm4+138>
        <+51>:  mov    edx,DWORD PTR [ebp-0x8]
        <+54>:  mov    eax,DWORD PTR [ebp+0x8]
        <+57>:  add    eax,edx
        <+59>:  movzx  eax,BYTE PTR [eax]
        <+62>:  movsx  edx,al
        <+65>:  mov    eax,DWORD PTR [ebp-0x8]
        <+68>:  lea    ecx,[eax-0x1]
        <+71>:  mov    eax,DWORD PTR [ebp+0x8]
        <+74>:  add    eax,ecx
        <+76>:  movzx  eax,BYTE PTR [eax]
        <+79>:  movsx  eax,al
        <+82>:  sub    edx,eax
        <+84>:  mov    eax,edx
        <+86>:  mov    edx,eax
        <+88>:  mov    eax,DWORD PTR [ebp-0x10]
        <+91>:  lea    ebx,[edx+eax*1]
        <+94>:  mov    eax,DWORD PTR [ebp-0x8]
        <+97>:  lea    edx,[eax+0x1]
        <+100>: mov    eax,DWORD PTR [ebp+0x8]
        <+103>: add    eax,edx
        <+105>: movzx  eax,BYTE PTR [eax]
        <+108>: movsx  edx,al
        <+111>: mov    ecx,DWORD PTR [ebp-0x8]
        <+114>: mov    eax,DWORD PTR [ebp+0x8]
        <+117>: add    eax,ecx
        <+119>: movzx  eax,BYTE PTR [eax]
        <+122>: movsx  eax,al
        <+125>: sub    edx,eax
        <+127>: mov    eax,edx
        <+129>: add    eax,ebx
        <+131>: mov    DWORD PTR [ebp-0x10],eax
        <+134>: add    DWORD PTR [ebp-0x8],0x1
        <+138>: mov    eax,DWORD PTR [ebp-0xc]
        <+141>: sub    eax,0x1
        <+144>: cmp    DWORD PTR [ebp-0x8],eax
        <+147>: jl     0x530 <asm4+51>
        <+149>: mov    eax,DWORD PTR [ebp-0x10]
        <+152>: add    esp,0x10
        <+155>: pop    ebx
        <+156>: pop    ebp
        <+157>: ret    


```

- Modificamos el código para que sea ejecutable

```asm
.intel_syntax noprefix
.global asm4


asm4:
        push   ebp
        mov    ebp,esp
        push   ebx
        sub    esp,0x10
        mov    DWORD PTR [ebp-0x10],0x27a
        mov    DWORD PTR [ebp-0xc],0x0
        jmp    asm4+27
        add    DWORD PTR [ebp-0xc],0x1
        mov    edx,DWORD PTR [ebp-0xc]
        mov    eax,DWORD PTR [ebp+0x8]
        add    eax,edx
        movzx  eax,BYTE PTR [eax]
        test   al,al
        jne    asm4+23
        mov    DWORD PTR [ebp-0x8],0x1
        jmp    asm4+138
        mov    edx,DWORD PTR [ebp-0x8]
        mov    eax,DWORD PTR [ebp+0x8]
        add    eax,edx
        movzx  eax,BYTE PTR [eax]
        movsx  edx,al
        mov    eax,DWORD PTR [ebp-0x8]
        lea    ecx,[eax-0x1]
        mov    eax,DWORD PTR [ebp+0x8]
        add    eax,ecx
        movzx  eax,BYTE PTR [eax]
        movsx  eax,al
        sub    edx,eax
        mov    eax,edx
        mov    edx,eax
        mov    eax,DWORD PTR [ebp-0x10]
        lea    ebx,[edx+eax*1]
        mov    eax,DWORD PTR [ebp-0x8]
        lea    edx,[eax+0x1]
        mov    eax,DWORD PTR [ebp+0x8]
        add    eax,edx
        movzx  eax,BYTE PTR [eax]
        movsx  edx,al
        mov    ecx,DWORD PTR [ebp-0x8]
        mov    eax,DWORD PTR [ebp+0x8]
        add    eax,ecx
        movzx  eax,BYTE PTR [eax]
        movsx  eax,al
        sub    edx,eax
        mov    eax,edx
        add    eax,ebx
        mov    DWORD PTR [ebp-0x10],eax
        add    DWORD PTR [ebp-0x8],0x1
        mov    eax,DWORD PTR [ebp-0xc]
        sub    eax,0x1
        cmp    DWORD PTR [ebp-0x8],eax
        jl     asm4+51
        mov    eax,DWORD PTR [ebp-0x10]
        add    esp,0x10
        pop    ebx
        pop    ebp
        ret    


```

- Hacemos un código en C que ejecutará el código en ensamblador.
```c
#include <stdio.h>

int main(){
        printf("Flag: 0x%x\n", asm4("picoCTF_f97bb"));
}

```

- Con la libreria gcc compilamos ambos archivos y despues los ejecutamos encadenados
```bash
┌──(kali㉿kali)-[~/picoCTF/reversin4]
└─$ gcc -m32 -c chal.s -o chal.o    


┌──(kali㉿kali)-[~/picoCTF/reversin4]
└─$ gcc -m32 -c solve.c -o solve.o -w -fpermissive
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/reversin4]
└─$ gcc -m32 -o a.out chal.o solve.o              
/usr/bin/ld: warning: chal.o: missing .note.GNU-stack section implies executable stack
/usr/bin/ld: NOTE: This behaviour is deprecated and will be removed in a future version of the linker
                                                                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/reversin4]
└─$ ./a.out 
Flag: 0x265

```
## Notas Adicionales
`gdb` (GNU Debugger) es una herramienta de depuración de código para programas escritos en lenguajes como C, C++ y ensamblador.

`gcc` (GNU Compiler Collection) es un conjunto de compiladores que convierte código fuente escrito en lenguajes como C, C++, y otros en código máquina ejecutable, que el sistema puede ejecutar directamente.
## Referencias