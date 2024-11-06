## Objetivo
What does asm1(0x2e0) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://jupiter.challenges.picoctf.org/static/f1c2358ff7d1e9386e41552c549cf2f6/test.S)
## Solución


```
asm1:
        <+0>:   push   ebp
        <+1>:   mov    ebp,esp
        <+3>:   cmp    DWORD PTR [ebp+0x8],0x3fb  va a traerse 4 bytes al mismo tiempo
        <+10>:  jg     0x512 <asm1+37>
        <+12>:  cmp    DWORD PTR [ebp+0x8],0x280 comparar
        <+19>:  jne    0x50a <asm1+29> condicion
        <+21>:  mov    eax,DWORD PTR [ebp+0x8]
        <+24>:  add    eax,0xa
        <+27>:  jmp    0x529 <asm1+60>
        <+29>:  mov    eax,DWORD PTR [ebp+0x8]
        <+32>:  sub    eax,0xa
        <+35>:  jmp    0x529 <asm1+60>
        <+37>:  cmp    DWORD PTR [ebp+0x8],0x559
        <+44>:  jne    0x523 <asm1+54>
        <+46>:  mov    eax,DWORD PTR [ebp+0x8]
        <+49>:  sub    eax,0xa
        <+52>:  jmp    0x529 <asm1+60>
        <+54>:  mov    eax,DWORD PTR [ebp+0x8]
        <+57>:  add    eax,0xa
        <+60>:  pop    ebp 
        <+61>:  ret    

```
El codigo es una pila
```s
stack
00000


[ebp] < ebp < esp
[ret] ebp + 0x4
[0x2e0] ebp + 0x8
fffff
Registers 
[0x2d6] eax
asm1(0x2e0):
        <+0>:   push   ebp
        <+1>:   mov    ebp,esp
        <+3>:   cmp    DWORD PTR [ebp+0x8],0x3fb
        <+10>:  jg     0x512 <asm1+37>
        <+12>:  cmp    DWORD PTR [ebp+0x8],0x280
        <+19>:  jne    0x50a <asm1+29>
        <+21>:  mov    eax,DWORD PTR [ebp+0x8]
        <+24>:  add    eax,0xa
        <+27>:  jmp    0x529 <asm1+60>
        <+29>:  mov    eax,DWORD PTR [ebp+0x8]
        <+32>:  sub    eax,0xa
        <+35>:  jmp    0x529 <asm1+60>
        <+37>:  cmp    DWORD PTR [ebp+0x8],0x559
        <+44>:  jne    0x523 <asm1+54>
        <+46>:  mov    eax,DWORD PTR [ebp+0x8]
        <+49>:  sub    eax,0xa
        <+52>:  jmp    0x529 <asm1+60>
        <+54>:  mov    eax,DWORD PTR [ebp+0x8]
        <+57>:  add    eax,0xa
        <+60>:  pop    ebp
        <+61>:  ret    

```
Ejecutammos el programa a mano y con python realizamos la comparaciones que el el codigo va realizando
```python
Python 3.12.6 (main, Sep  7 2024, 14:20:15) [GCC 14.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 0x2e0 > 0x3fb
False
>>> 0x2e0 != 0x280
True
>>> hex(0x2e0 - 0xa)
'0x2d6'
>>> 

```
## Notas Adicionales

|                        |                                                                                                |
| ---------------------- | ---------------------------------------------------------------------------------------------- |
| mov BYTE PTR [ebx], 2  | ; Move 2 into the single byte at the address stored in EBX.                                    |
| mov WORD PTR [ebx], 2  | ; Move the 16-bit integer representation of 2 into the 2 bytes starting at the address in EBX. |
| mov DWORD PTR [ebx], 2 | ; Move the 32-bit integer representation of 2 into the 4 bytes starting at the address in EBX. |
|                        |                                                                                                |
Registros
![[Pasted image 20241105185505.png]]


```
Syntax  
je <label> (jump when equal)  
jne <label> (jump when not equal)  
jz <label> (jump when last result was zero)  
jg <label> (jump when greater than)  
jge <label> (jump when greater than or equal to)  
jl <label> (jump when less than)  
jle <label> (jump when less than or equal to)
```

## Referencias
https://www.cs.virginia.edu/~evans/cs216/guides/x86.html