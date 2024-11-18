## Objetivo
Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`.Download the assembly dump [here](https://artifacts.picoctf.net/c/530/disassembler-dump0_c.txt).
## Solución
```bash
<+0>:     endbr64 
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x14],edi
<+11>:    mov    QWORD PTR [rbp-0x20],rsi
<+15>:    mov    DWORD PTR [rbp-0xc],0x9fe1a
<+22>:    mov    DWORD PTR [rbp-0x8],0x4
<+29>:    mov    eax,DWORD PTR [rbp-0xc]
<+32>:    imul   eax,DWORD PTR [rbp-0x8]
<+36>:    add    eax,0x1f5
<+41>:    mov    DWORD PTR [rbp-0x4],eax
<+44>:    mov    eax,DWORD PTR [rbp-0x4]
<+47>:    pop    rbp
<+48>:    ret
```

Esto es lo que ejecuta el cpu:
```
<+15>: Se almacena el valor DWORD 654874 en la ubicación de memoria apuntada por [rbp-0xc]
<+22>: Se almacena el valor DWORD 4 en la ubicación de memoria apuntada por [rbp-0x8]
<+29>: El valor almacenado en la ubicación de memoria apuntada por [rbp-0xc] (654874) se almacena en el registro eax
<+32>: El valor almacenado en el registro eax se multiplica con el valor almacenado en la ubicación de memoria apuntada por [rbp-0x8] (4) y el resultado se almacena en el registro eax
<+36>: El valor 501 se suma al valor almacenado en el registro eax y el resultado se almacena en el registro eax
<+41>: El valor almacenado en el registro eax se almacena en la ubicación de memoria apuntada por [rbp-0x4]
<+44>: El valor en la ubicación de memoria apuntada por [rbp-0x4] se almacena en el registro eax

```

```python
Python 3.11.4 (main, Jun  7 2023, 10:13:09) [GCC 12.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> (0x9fe1a * 0x4) + 0x1f5
2619997
>>>
```
## Notas Adicionales

## Referencias
