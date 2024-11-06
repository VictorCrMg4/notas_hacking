## Objetivo
What does asm2(0x4,0x2d) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://jupiter.challenges.picoctf.org/static/ceac75672637589213b952abe32c84b3/test.S)
## Solución
```asm
[] < esp
[] ebp - 0xc
[0x4] ebp - 0x8
[0x3d] ebp - 0x4 - local1

[ebp] < ebp 

[0x3d] ebp + 0xc

[0x4]eax

asm2(0x4,0x2d):
        <+0>:   push   ebp
        <+1>:   mov    ebp,esp

        <+3>:   sub    esp,0x10
        <+6>:   mov    eax,DWORD PTR [ebp+0xc]
        <+9>:   mov    DWORD PTR [ebp-0x4],eax
        <+12>:  mov    eax,DWORD PTR [ebp+0x8]
        <+15>:  mov    DWORD PTR [ebp-0x8],eax
        <+18>:  jmp    0x50c <asm2+31>
        <+20>:  add    DWORD PTR [ebp-0x4],0x1
        <+24>:  add    DWORD PTR [ebp-0x8],0xd1
        <+31>:  cmp    DWORD PTR [ebp-0x8],0x5fa1
        <+38>:  jle    0x501 <asm2+20>
        <+40>:  mov    eax,DWORD PTR [ebp-0x4]

        <+43>:  leave  
        <+44>:  ret    


```
Obtenemos el número de veces que el programa tiene que hacer el ciclo para poder salirse, a ese valor le sumamos el valor entero de 0x2d y a eso le sumamos el número de las vueltas que obtuvimos, al resultado convertimos a hexadecimal.
```python
Python 3.12.6 (main, Sep  7 2024, 14:20:15) [GCC 14.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 0x4 <= 0x5fa1
True
>>> hex(0x3d + 0x1)
'0x3e'
>>> 0x4 - 0xd1
-205
>>> import numpy
>>> numpy.int32(0xd1)
209
>>> 0x5fa1 / 128
191.2578125
>>> int (0x4)
4
>>> 0x5fa1 / 209
117.13397129186603
>>> 0x5fa1 / 0xd1
117.13397129186603
>>> int (0x2d)
45
>>> 45 +118
163
>>> hex(163)
'0xa3'

```
## Notas Adicionales

## Referencias