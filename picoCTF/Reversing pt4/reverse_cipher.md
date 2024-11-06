## Objetivo
We have recovered a [binary](https://jupiter.challenges.picoctf.org/static/7aa5f383ec616fe9d72c2ffe1fabd0d9/rev) and a [text file](https://jupiter.challenges.picoctf.org/static/7aa5f383ec616fe9d72c2ffe1fabd0d9/rev_this). Can you reverse the flag.
## Solución
Vemos el programa en binario, pero vamos a usar ghidra para obtener un codigo en c que haga lo mismo.
```bash
┌──(kali㉿kali)-[~/picoCTF/reversin4]
└─$ gdb -q rev           
Reading symbols from rev...
(No debugging symbols found in rev)
(gdb) info functions
All defined functions:

Non-debugging symbols:
0x0000000000001000  _init
0x0000000000001030  puts@plt
0x0000000000001040  fread@plt
0x0000000000001050  fclose@plt
0x0000000000001060  fputc@plt
0x0000000000001070  fopen@plt
0x0000000000001080  exit@plt
0x0000000000001090  __cxa_finalize@plt
0x00000000000010a0  _start
0x00000000000010d0  deregister_tm_clones
--Type <RET> for more, q to quit, c to continue without paging--
0x0000000000001100  register_tm_clones
0x0000000000001140  __do_global_dtors_aux
0x0000000000001180  frame_dummy
0x0000000000001185  main
0x00000000000012d0  __libc_csu_init
0x0000000000001330  __libc_csu_fini
0x0000000000001334  _fini
(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000001185 <+0>:     push   %rbp
   0x0000000000001186 <+1>:     mov    %rsp,%rbp
   0x0000000000001189 <+4>:     sub    $0x50,%rsp
   0x000000000000118d <+8>:     lea    0xe74(%rip),%rsi        # 0x2008
   0x0000000000001194 <+15>:    lea    0xe6f(%rip),%rdi        # 0x200a
   0x000000000000119b <+22>:    call   0x1070 <fopen@plt>
   0x00000000000011a0 <+27>:    mov    %rax,-0x18(%rbp)
   0x00000000000011a4 <+31>:    lea    0xe68(%rip),%rsi        # 0x2013
   0x00000000000011ab <+38>:    lea    0xe63(%rip),%rdi        # 0x2015
   0x00000000000011b2 <+45>:    call   0x1070 <fopen@plt>
   0x00000000000011b7 <+50>:    mov    %rax,-0x20(%rbp)
   0x00000000000011bb <+54>:    cmpq   $0x0,-0x18(%rbp)
--Type <RET> for more, q to quit, c to continue without paging--
   0x00000000000011c0 <+59>:    jne    0x11ce <main+73>
   0x00000000000011c2 <+61>:    lea    0xe57(%rip),%rdi        # 0x2020
   0x00000000000011c9 <+68>:    call   0x1030 <puts@plt>
   0x00000000000011ce <+73>:    cmpq   $0x0,-0x20(%rbp)
   0x00000000000011d3 <+78>:    jne    0x11e1 <main+92>
   0x00000000000011d5 <+80>:    lea    0xe7e(%rip),%rdi        # 0x205a
   0x00000000000011dc <+87>:    call   0x1030 <puts@plt>
   0x00000000000011e1 <+92>:    mov    -0x18(%rbp),%rdx
   0x00000000000011e5 <+96>:    lea    -0x50(%rbp),%rax
   0x00000000000011e9 <+100>:   mov    %rdx,%rcx
   0x00000000000011ec <+103>:   mov    $0x1,%edx
   0x00000000000011f1 <+108>:   mov    $0x18,%esi
   0x00000000000011f6 <+113>:   mov    %rax,%rdi
--Type <RET> for more, q to quit, c to continue without paging--
   0x00000000000011f9 <+116>:   call   0x1040 <fread@plt>
   0x00000000000011fe <+121>:   mov    %eax,-0x24(%rbp)
   0x0000000000001201 <+124>:   cmpl   $0x0,-0x24(%rbp)
   0x0000000000001205 <+128>:   jg     0x1211 <main+140>
   0x0000000000001207 <+130>:   mov    $0x0,%edi
   0x000000000000120c <+135>:   call   0x1080 <exit@plt>
   0x0000000000001211 <+140>:   movl   $0x0,-0x8(%rbp)
   0x0000000000001218 <+147>:   jmp    0x123d <main+184>
   0x000000000000121a <+149>:   mov    -0x8(%rbp),%eax
   0x000000000000121d <+152>:   cltq
   0x000000000000121f <+154>:   movzbl -0x50(%rbp,%rax,1),%eax
   0x0000000000001224 <+159>:   mov    %al,-0x1(%rbp)
   0x0000000000001227 <+162>:   movsbl -0x1(%rbp),%eax
--Type <RET> for more, q to quit, c to continue without paging--
   0x000000000000122b <+166>:   mov    -0x20(%rbp),%rdx
   0x000000000000122f <+170>:   mov    %rdx,%rsi
   0x0000000000001232 <+173>:   mov    %eax,%edi
   0x0000000000001234 <+175>:   call   0x1060 <fputc@plt>
   0x0000000000001239 <+180>:   addl   $0x1,-0x8(%rbp)
   0x000000000000123d <+184>:   cmpl   $0x7,-0x8(%rbp)
   0x0000000000001241 <+188>:   jle    0x121a <main+149>
   0x0000000000001243 <+190>:   movl   $0x8,-0xc(%rbp)
   0x000000000000124a <+197>:   jmp    0x128f <main+266>
   0x000000000000124c <+199>:   mov    -0xc(%rbp),%eax
   0x000000000000124f <+202>:   cltq
   0x0000000000001251 <+204>:   movzbl -0x50(%rbp,%rax,1),%eax
   0x0000000000001256 <+209>:   mov    %al,-0x1(%rbp)
--Type <RET> for more, q to quit, c to continue without paging--
   0x0000000000001259 <+212>:   mov    -0xc(%rbp),%eax
   0x000000000000125c <+215>:   and    $0x1,%eax
   0x000000000000125f <+218>:   test   %eax,%eax
   0x0000000000001261 <+220>:   jne    0x126f <main+234>
   0x0000000000001263 <+222>:   movzbl -0x1(%rbp),%eax
   0x0000000000001267 <+226>:   add    $0x5,%eax
   0x000000000000126a <+229>:   mov    %al,-0x1(%rbp)
   0x000000000000126d <+232>:   jmp    0x1279 <main+244>
   0x000000000000126f <+234>:   movzbl -0x1(%rbp),%eax
   0x0000000000001273 <+238>:   sub    $0x2,%eax
   0x0000000000001276 <+241>:   mov    %al,-0x1(%rbp)
   0x0000000000001279 <+244>:   movsbl -0x1(%rbp),%eax
   0x000000000000127d <+248>:   mov    -0x20(%rbp),%rdx
--Type <RET> for more, q to quit, c to continue without paging--
   0x0000000000001281 <+252>:   mov    %rdx,%rsi
   0x0000000000001284 <+255>:   mov    %eax,%edi
   0x0000000000001286 <+257>:   call   0x1060 <fputc@plt>
   0x000000000000128b <+262>:   addl   $0x1,-0xc(%rbp)
   0x000000000000128f <+266>:   cmpl   $0x16,-0xc(%rbp)
   0x0000000000001293 <+270>:   jle    0x124c <main+199>
   0x0000000000001295 <+272>:   movzbl -0x39(%rbp),%eax
   0x0000000000001299 <+276>:   mov    %al,-0x1(%rbp)
   0x000000000000129c <+279>:   movsbl -0x1(%rbp),%eax
   0x00000000000012a0 <+283>:   mov    -0x20(%rbp),%rdx
   0x00000000000012a4 <+287>:   mov    %rdx,%rsi
   0x00000000000012a7 <+290>:   mov    %eax,%edi
   0x00000000000012a9 <+292>:   call   0x1060 <fputc@plt>
--Type <RET> for more, q to quit, c to continue without paging--
   0x00000000000012ae <+297>:   mov    -0x20(%rbp),%rax
   0x00000000000012b2 <+301>:   mov    %rax,%rdi
   0x00000000000012b5 <+304>:   call   0x1050 <fclose@plt>
   0x00000000000012ba <+309>:   mov    -0x18(%rbp),%rax
   0x00000000000012be <+313>:   mov    %rax,%rdi
   0x00000000000012c1 <+316>:   call   0x1050 <fclose@plt>
   0x00000000000012c6 <+321>:   nop
   0x00000000000012c7 <+322>:   leave
   0x00000000000012c8 <+323>:   ret
End of assembler dump.
(gdb) 

```
Analizamos el código con Ghidra 

![[Pasted image 20241106115532.png]]



```c
void main(void)

{
  size_t sVar1;
  char local_58 [23];
  char local_41;
  int local_2c;
  FILE *local_28;
  FILE *local_20;
  uint local_14;
  int local_10;
  char local_9;
  
  local_20 = fopen("flag.txt","r");
  local_28 = fopen("rev_this","a");
  if (local_20 == (FILE *)0x0) {
    puts("No flag found, please make sure this is run on the server");
  }
  if (local_28 == (FILE *)0x0) {
    puts("please run this on the server");
  }
  sVar1 = fread(local_58,0x18,1,local_20);
  local_2c = (int)sVar1;
  if ((int)sVar1 < 1) {
                    /* WARNING: Subroutine does not return */
    exit(0);
  }
  for (local_10 = 0; local_10 < 8; local_10 = local_10 + 1) {
    local_9 = local_58[local_10];
    fputc((int)local_9,local_28);
  }
  for (local_14 = 8; (int)local_14 < 0x17; local_14 = local_14 + 1) {
    if ((local_14 & 1) == 0) {
      local_9 = local_58[(int)local_14] + '\x05';
    }
    else {
      local_9 = local_58[(int)local_14] + -2;
    }
    fputc((int)local_9,local_28);
  }
  local_9 = local_41;
  fputc((int)local_41,local_28);
  fclose(local_28);
  fclose(local_20);
  return;
}

```
Usamos python para convertir lo que hacen los for
```python
rev = open('rev_this').read()

flag=''

for i in range(8):
        flag += rev[i]

for j in range(8,24):
        if j&1 ==0:
                flag += chr(ord(rev[j])-5)
        else:
                flag += chr(ord(rev[j])+2)
flag += rev[23]
print(flag)


```
Ejecutamos el código
```bash
┌──(kali㉿kali)-[~/picoCTF/reversin4]
└─$ python3 solve.py 
picoCTF{r3v3rs36ad73964}

```
## Notas Adicionales
Ghidra es una herramienta de ingeniería inversa gratuita y de código abierto desarrollada por la Agencia de Seguridad Nacional de los Estados Unidos

`gdb` (GNU Debugger) es una herramienta de depuración de código para programas escritos en lenguajes como C, C++ y ensamblador.
## Referencias
