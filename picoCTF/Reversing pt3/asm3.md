## Objetivo
What does asm3(0xd2c26416,0xe6cf51f0,0xe54409d5) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. Source
## Solución
```bash
sm3:
        <+0>:   push   ebp
        <+1>:   mov    ebp,esp
        <+3>:   xor    eax,eax
        <+5>:   mov    ah,BYTE PTR [ebp+0x9]
        <+8>:   shl    ax,0x10
        <+12>:  sub    al,BYTE PTR [ebp+0xe]
        <+15>:  add    ah,BYTE PTR [ebp+0xf]
        <+18>:  xor    ax,WORD PTR [ebp+0x12]
        <+22>:  nop
        <+23>:  pop    ebp
        <+24>:  ret    


```

```bash
┌──(kali㉿kali)-[~/picoCTF/reversing3]
└─$ cat test.S.2 | cut -d ':' -f 2

        push   ebp
        mov    ebp,esp
        xor    eax,eax
        mov    ah,BYTE PTR [ebp+0x9]
        shl    ax,0x10
        sub    al,BYTE PTR [ebp+0xe]
        add    ah,BYTE PTR [ebp+0xf]
        xor    ax,WORD PTR [ebp+0x12]
        nop
        pop    ebp
        ret    

```

Entramos al emulador y nos vamos a la primera linea y le damos Step hasta a linea 16

![[Pasted image 20241104114639.png]]

La bandera esta en EAX
## Notas Adicionales

## Referencias
https://carlosrafaelgn.com.br/Asm86/