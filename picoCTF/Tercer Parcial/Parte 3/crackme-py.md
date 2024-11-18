## Objetivo
[crackme.py](https://mercury.picoctf.net/static/2ff6c888060f14af5db1232e319547c9/crackme.py)
## Solución

Nos dan este codigo que al eecutarlo simplememnte nos devuelve el numero mayor de entre 2 numero que le damos, pero podemos revisar que hay una seccion a parte que realiza otras cosas. Lo que hace decode_secret es que simplemente hace un ROT47 a lo que se le da como parametro.
```python
# Hiding this really important number in an obscure piece of code is brilliant!

# AND it's encrypted!

# We want our biggest client to know his information is safe with us.

bezos_cc_secret = "A:4@r%uL`M-^M0c0AbcM-MFE067d3eh2bN"

  

# Reference alphabet

alphabet = "!\"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ"+ \

            "[\\]^_`abcdefghijklmnopqrstuvwxyz{|}~"

  
  
  

def decode_secret(secret):

    """ROT47 decode

  

    NOTE: encode and decode are the same operation in the ROT cipher family.

    """

  

    # Encryption key

    rotate_const = 47

  

    # Storage for decoded secret

    decoded = ""

  

    # decode loop

    for c in secret:

        index = alphabet.find(c)

        original_index = (index + rotate_const) % len(alphabet)

        decoded = decoded + alphabet[original_index]

  

    print(decoded)

  

decode_secret(bezos_cc_secret)

  

def choose_greatest():

    """Echo the largest of the two numbers given by the user to the program

  

    Warning: this function was written quickly and needs proper error handling

    """

  

    user_value_1 = input("What's your first number? ")

    user_value_2 = input("What's your second number? ")

    greatest_value = user_value_1 # need a value to return if 1 & 2 are equal

  

    if user_value_1 > user_value_2:

        greatest_value = user_value_1

    elif user_value_1 < user_value_2:

        greatest_value = user_value_2

  

    print( "The number with largest positive magnitude is "

        + str(greatest_value) )

  
  
  

#choose_greatest()
```

Asi entonces, modificamos el codigo para decodificar la contraseña
```python
# Hiding this really important number in an obscure piece of code is brilliant!

# AND it's encrypted!

# We want our biggest client to know his information is safe with us.

bezos_cc_secret = "A:4@r%uL`M-^M0c0AbcM-MFE067d3eh2bN"

  

# Reference alphabet

alphabet = "!\"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ"+ \

            "[\\]^_`abcdefghijklmnopqrstuvwxyz{|}~"

  
  
  

def decode_secret(secret):

    """ROT47 decode

  

    NOTE: encode and decode are the same operation in the ROT cipher family.

    """

  

    # Encryption key

    rotate_const = 47

  

    # Storage for decoded secret

    decoded = ""

  

    # decode loop

    for c in secret:

        index = alphabet.find(c)

        original_index = (index + rotate_const) % len(alphabet)

        decoded = decoded + alphabet[original_index]

  

    print(decoded)

  

decode_secret(bezos_cc_secret)

  

def choose_greatest():

    """Echo the largest of the two numbers given by the user to the program

  

    Warning: this function was written quickly and needs proper error handling

    """

  

    user_value_1 = input("What's your first number? ")

    user_value_2 = input("What's your second number? ")

    greatest_value = user_value_1 # need a value to return if 1 & 2 are equal

  

    if user_value_1 > user_value_2:

        greatest_value = user_value_1

    elif user_value_1 < user_value_2:

        greatest_value = user_value_2

  

    print( "The number with largest positive magnitude is "

        + str(greatest_value) )

  
  
  

#choose_greatest()
```

```bash
PS C:\Users\VICTOR CORREA> & "C:/Users/VICTOR CORREA/AppData/Local/Programs/Python/Python311/python.exe" "c:/Users/VICTOR CORREA/Downloads/crackme.py"
picoCTF{1|\/|_4_p34|\|ut_ef5b69a3}
```
## Notas Adicionales

## Referencias
