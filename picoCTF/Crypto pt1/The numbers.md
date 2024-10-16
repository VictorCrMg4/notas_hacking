## Objetivo

The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?
![[the_numbers.png]]
## Solución

```bash
victormcm-picoctf@webshell:~$ echo "16 9 3 15 3 29 6 20 8 5 14 21 13 2 5 18 19 13 1 19 15 14" | awk '{for(i=1; i<=NF; i++) printf "%c", ((($i - 1) % 26) + 65); print ""}'
PICOCTFTHENUMBERSMASON
```
## Notas Adicionales

## Referencias