## Objetivo
Attackers have hidden information in a very large mass of data in the past, maybe they are still doing it.Download the data [here](https://artifacts.picoctf.net/c/125/anthem.flag.txt).
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF/lookeyhere]
└─$ cat anthem.flag.txt 
      ANTHEM

      by Ayn Rand


        CONTENTS

         PART ONE

         PART TWO

         PART THREE

         PART FOUR

         PART FIVE

         PART SIX

         PART SEVEN

         PART EIGHT

         PART NINE

         PART TEN

         PART ELEVEN

         PART TWELVE




      PART ONE

      It is a sin to write this. It is a sin to think words no others
      think and to put them down upon a paper no others are to see. It
      is base and evil. It is as if we were speaking alone to no ears
      but our own. And we know well that there is no transgression
      blacker than to do or think alone. We have broken the laws. The
      laws say that men may not write unless the Council of Vocations
      bid them so. May we be forgiven!

      But this is not the only sin upon us. We have committed a greater
      crime, and for this crime there is no name. What punishment
      awaits us if it be discovered we know not, for no such crime has
      come in the memory of men and there are no laws to provide for
      it.
....
┌──(kali㉿kali)-[~/picoCTF/lookeyhere]
└─$ cat anthem.flag.txt | grep pico     
      we think that the men of picoCTF{gr3p_15_@w3s0m3_58f5c024}


```
## Notas Adicionales

## Referencias
