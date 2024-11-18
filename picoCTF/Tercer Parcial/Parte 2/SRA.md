## Objetivo
I just recently learnt about the SRA public key cryptosystem... or wait, was it supposed to be RSA? Hmmm, I should probably check...Connect to the program on our server: `nc saturn.picoctf.net 55055`Download the program: [chal.py](https://artifacts.picoctf.net/c/295/chal.py)
## Solución
```python
from Crypto.Util.number import getPrime, inverse, bytes_to_long
from string import ascii_letters, digits
from random import choice

pride = "".join(choice(ascii_letters + digits) for _ in range(16))
gluttony = getPrime(128)
greed = getPrime(128)
lust = gluttony * greed
sloth = 65537
envy = inverse(sloth, (gluttony - 1) * (greed - 1))

anger = pow(bytes_to_long(pride.encode()), sloth, lust)

print(f"{anger = }")
print(f"{envy = }")

print("vainglory?")
vainglory = input("> ").strip()

if vainglory == pride:
    print("Conquered!")
    with open("/challenge/flag.txt") as f:
        print(f.read())
else:
    print("Hubris!")

```
Se nos proporciona un texto cifrado y el valor de d, pero no se nos proporciona n. Sabiendo que e\*d mod (p-1)(q-1)=1, y que p y q son primos de 128 bits, obtenemos una lista potencial de valores p y q, y luego intentamos descifrar con cada n posible. El que sale como texto simple es correcto, y luego el programa nos da la bandera.

### Creación del entorno e instalación de librerías
```bash
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte2]
└─$ python3 -m venv venv
                                                                                 
┌──(kali㉿kali)-[~/picoCTF/tercerparcial/parte2]
└─$ source venv/bin/activate
                                                                                 
┌──(venv)─(kali㉿kali)-[~/picoCTF/tercerparcial/parte2]
└─$ pip install primefac
Collecting primefac
  Using cached primefac-2.0.12-py3-none-any.whl.metadata (13 kB)
Using cached primefac-2.0.12-py3-none-any.whl (54 kB)
Installing collected packages: primefac
Successfully installed primefac-2.0.12                            
                                                                                 
┌──(venv)─(kali㉿kali)-[~/picoCTF/tercerparcial/parte2]
└─$ pip install sympy    
Collecting sympy
  Downloading sympy-1.13.3-py3-none-any.whl.metadata (12 kB)
Collecting mpmath<1.4,>=1.1.0 (from sympy)
  Downloading mpmath-1.3.0-py3-none-any.whl.metadata (8.6 kB)
Downloading sympy-1.13.3-py3-none-any.whl (6.2 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 6.2/6.2 MB 8.5 MB/s eta 0:00:00
Downloading mpmath-1.3.0-py3-none-any.whl (536 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 536.2/536.2 kB 4.0 MB/s eta 0:00:00
Installing collected packages: mpmath, sympy
Successfully installed mpmath-1.3.0 sympy-1.13.3
                                                                                 
┌──(venv)─(kali㉿kali)-[~/picoCTF/tercerparcial/parte2]
└─$ pip install pycryptodome
Collecting pycryptodome
  Downloading pycryptodome-3.21.0-cp36-abi3-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (3.4 kB)
Downloading pycryptodome-3.21.0-cp36-abi3-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (2.3 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 2.3/2.3 MB 11.2 MB/s eta 0:00:00
Installing collected packages: pycryptodome
Successfully installed pycryptodome-3.21.0
                                                                         
┌──(venv)─(kali㉿kali)-[~/picoCTF/tercerparcial/parte2]
└─$ pip install pwntools
Collecting pwntools
  Using cached pwntools-4.13.1-py2.py3-none-any.whl.metadata (5.3 kB)
Collecting paramiko>=1.15.2 (from pwntools)
  Using cached paramiko-3.5.0-py3-none-any.whl.metadata (4.4 kB)
....
                                                                                                                                                          
┌──(venv)─(kali㉿kali)-[~/picoCTF/tercerparcial/parte2]
└─$ nano solve.py    

```

solve.py
Este recibe un mensaje cifrado (`ciphertext`) y una clave privada parcial (`d`), y luego intenta factorizar n=p×qn = p \times qn=p×q utilizando divisores de d×e−1d \times e - 1d×e−1 para encontrar los primos ppp y qqq. Prueba diferentes combinaciones de factores como posibles valores de p−1p-1p−1 y q−1q-1q−1, y usa estos valores para descifrar el mensaje. Finalmente, si obtiene un descifrado legible, lo envía al servidor para completar el desafío.
```python
from pwn import *
import primefac
from itertools import combinations
from Crypto.Util.number import long_to_bytes

#function to generate all the sub lists
def sub_lists (l):
    #initializing empty list
    comb = []

    #Iterating till length of list
    for i in range(1,len(l)+1):
        #Generating sub list
        comb += [list(j) for j in combinations(l, i)]
    #Returning list
    return comb

def divisors(phi):
   print("Give me the divisors of ", phi-1)
   #this is dangerous, but I'm trusting me
   return(eval(input()))

#connect to the server
r = remote('saturn.picoctf.net', 57848)
#get ciphertext
r.recvuntil("anger =")
ciphertext=int(r.recvline())
#get d
r.recvuntil("envy =")
d=int(r.recvline())
print("cipher=",ciphertext)
print("d=",d)
print(r.recvuntil("vainglory?"))
r.recvline()
#since d is e^-1 mod (p-1)*(q-1), d*e=k*(p-1)*(q-1)+1
#so (p-1)*(q-1)*k = d*e-1
factors=divisors(d*65537)
combos = sub_lists(factors)
primes = set()
#try all possible subsets of the list of factors as the factors of (p-1)
for l in combos:
   product = 1
   #multiply them together to get p-1
   for k in l:
      product = product * k
   #if the right length and adding 1 yields a prime, then maybe
   if product.bit_length()==128 and primefac.isprime(product+1):
      primes.add(product+1)
print(primes)
primelist = list(primes)
#try all possible prime pairs
for p in primelist:
   for q in primelist:
      n=p*q
      #decode with this possible n
      plain = pow(ciphertext,d,n)
      try:
         plaintext = long_to_bytes(plain)
         #see if it corresponds to text and if so, try it
         print(plaintext.decode())
         r.sendline(plaintext.decode())
         print(r.recvline())
         print(r.recvline())
         print(r.recvline())
      except:
         continue


```

Ejecutamos el código
```bash                                                                        
┌──(venv)─(kali㉿kali)-[~/picoCTF/tercerparcial/parte2]
└─$ python3 solve.py
[+] Opening connection to saturn.picoctf.net on port 57848: Done
/home/kali/picoCTF/tercerparcial/parte2/solve.py:26: BytesWarning: Text is not bytes; assuming ASCII, no guarantees. See https://docs.pwntools.com/#bytes
  r.recvuntil("anger =")
/home/kali/picoCTF/tercerparcial/parte2/solve.py:29: BytesWarning: Text is not bytes; assuming ASCII, no guarantees. See https://docs.pwntools.com/#bytes
  r.recvuntil("envy =")
cipher= 14683916585420247843249973555068446231408872791104965532768388603829087832038
d= 21973944274224657424484224711656107264283122621872425870451659335583714252497
/home/kali/picoCTF/tercerparcial/parte2/solve.py:33: BytesWarning: Text is not bytes; assuming ASCII, no guarantees. See https://docs.pwntools.com/#bytes
  print(r.recvuntil("vainglory?"))
b'vainglory?'
Give me the divisors of  1440106385899861373628422634927806301779323007269653174271790397876149880965895888
[2, 2, 2, 2, 3, 11, 23, 41, 97, 641, 1931, 2129, 3329, 7079, 476576473, 2628753711071, 61148842792697683, 6267651120379661011]
{171118159654335246315541329626656947857, 245661245016041684106741014716615259129, 245855057927450196269546210541837524389, 257332641645462512829894266698975976177, 201315477435858142552753131705317335453, 223057094789030550232761184183670032567, 189840191047139759918596466959770093589, 215359640563488035771820319270419552529, 227963249621013305635654887049834010587, 186840682966462025219523088924493731733, 251275396728640222800538648845190139597, 217264451780771157395582029332720580817}
ccwyi3kA6RtIdU44
/home/kali/picoCTF/tercerparcial/parte2/solve.py:61: BytesWarning: Text is not bytes; assuming ASCII, no guarantees. See https://docs.pwntools.com/#bytes
  r.sendline(plaintext.decode())
b'> ccwyi3kA6RtIdU44\r\n'
b'Conquered!\r\n'
b'picoCTF{7h053_51n5_4r3_n0_m0r3_2b7ad1ae}\r\n'
ccwyi3kA6RtIdU44
[*] Closed connection to saturn.picoctf.net port 57848

                                                          
```
Obtenemos los divisores de 1440106385899861373628422634927806301779323007269653174271790397876149880965895888 en esta pagina: https://www.dcode.fr/prime-factors-decomposition y los ponemos en forma de lista.
## Notas Adicionales

## Referencias
https://www.dcode.fr/prime-factors-decomposition