## Objetivo
How well can you perfom basic binary operations?

Additional details will be available after launching your challenge instance.
## Solución
```bash
victormcm-picoctf@webshell:~$ nc titan.picoctf.net 58144

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 11110011
Binary Number 2: 10000001


Question 1/6:
Operation 1: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 243 <<129

Incorrect input. Provide the right input
Enter the binary result: ^C
victormcm-picoctf@webshell:~$ nc titan.picoctf.net 58144

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 01101100
Binary Number 2: 00010010


Question 1/6:
Operation 1: '|'
Perform the operation on Binary Number 1&2.

Enter the binary result: 01111110         
Correct!

Question 2/6:
Operation 2: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 11011000
Incorrect. Try again
Enter the binary result: 1001
Correct!

Question 3/6:
Operation 3: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 01111110
Correct!

Question 4/6:
Operation 4: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 0
Correct!

Question 5/6:
Operation 5: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 011110011000
Correct!

Question 6/6:
Operation 6: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 11011000
Correct!

Enter the results of the last operation in hexadecimal: 798
Incorrect answer!

Enter the results of the last operation in hexadecimal: D8

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_6ab1ad84}
```
## Notas Adicionales

## Referencias
[Desplazamientos de bits](https://miniwebtool.com/es/bitwise-calculator/bit-shift/?data_type=2&number=01101100&place=1&operator=Shift+Left)