## Objetivo
This program has constructed the flag using hex ascii values. Identify the flag text by disassembling the program.You can download the file from [here](https://artifacts.picoctf.net/c/507/asciiftw).
## Solución
Abrimos el archivo en Ghidra
```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte3]
└─$ ghidra  
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true

```

En la seccion de listing podemos ver unos hexadecimales en fila, el valor de esos hexadecimales corresponde al valor de un caracter en el códdigo ascii
Le damos click derecho al valor hexadecimal > conver > char, para convertir el valor a un caracter.

![[Pasted image 20241114132023.png]]

Quedarian algo asi.
```bash
        00101184 c6 45 d0 70     MOV        byte ptr [RBP + local_38],'p'
        00101188 c6 45 d1 69     MOV        byte ptr [RBP + local_37],'i'
        0010118c c6 45 d2 63     MOV        byte ptr [RBP + local_36],'c'
        00101190 c6 45 d3 6f     MOV        byte ptr [RBP + local_35],'o'
        00101194 c6 45 d4 43     MOV        byte ptr [RBP + local_34],'C'
        00101198 c6 45 d5 54     MOV        byte ptr [RBP + local_33],'T'
        0010119c c6 45 d6 46     MOV        byte ptr [RBP + local_32],'F'
        001011a0 c6 45 d7 7b     MOV        byte ptr [RBP + local_31],'{'
        001011a4 c6 45 d8 41     MOV        byte ptr [RBP + local_30],'A'
        001011a8 c6 45 d9 53     MOV        byte ptr [RBP + local_2f],'S'
        001011ac c6 45 da 43     MOV        byte ptr [RBP + local_2e],'C'
        001011b0 c6 45 db 49     MOV        byte ptr [RBP + local_2d],'I'
        001011b4 c6 45 dc 49     MOV        byte ptr [RBP + local_2c],'I'
        001011b8 c6 45 dd 5f     MOV        byte ptr [RBP + local_2b],'_'
        001011bc c6 45 de 49     MOV        byte ptr [RBP + local_2a],'I'
        001011c0 c6 45 df 53     MOV        byte ptr [RBP + local_29],'S'
        001011c4 c6 45 e0 5f     MOV        byte ptr [RBP + local_28],'_'
        001011c8 c6 45 e1 45     MOV        byte ptr [RBP + local_27],'E'
        001011cc c6 45 e2 41     MOV        byte ptr [RBP + local_26],'A'
        001011d0 c6 45 e3 53     MOV        byte ptr [RBP + local_25],'S'
        001011d4 c6 45 e4 59     MOV        byte ptr [RBP + local_24],'Y'
        001011d8 c6 45 e5 5f     MOV        byte ptr [RBP + local_23],'_'
        001011dc c6 45 e6 37     MOV        byte ptr [RBP + local_22],'7'
        001011e0 c6 45 e7 42     MOV        byte ptr [RBP + local_21],'B'
        001011e4 c6 45 e8 43     MOV        byte ptr [RBP + local_20],'C'
        001011e8 c6 45 e9 44     MOV        byte ptr [RBP + local_1f],'D'
        001011ec c6 45 ea 39     MOV        byte ptr [RBP + local_1e],'9'
        001011f0 c6 45 eb 37     MOV        byte ptr [RBP + local_1d],'7'
        001011f4 c6 45 ec 31     MOV        byte ptr [RBP + local_1c],'1'
        001011f8 c6 45 ed 44     MOV        byte ptr [RBP + local_1b],'D'
        001011fc c6 45 ee 7d     MOV        byte ptr [RBP + local_1a],'}'
        00101200 0f b6 45 d0     MOVZX      EAX,byte ptr [RBP + local_38]
        00101204 0f be c0        MOVSX      EAX,AL

```

solo faltaria juntar las secciones de la bandera

`picoCTF{ASCII_IS_EASY_7BCD971D}`
## Notas Adicionales

## Referencias
