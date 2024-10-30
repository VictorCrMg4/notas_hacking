## Objetivo
This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: [VaultDoor1.java](https://jupiter.challenges.picoctf.org/static/ff2585f7afd21b81f69d2fbe37c081ae/VaultDoor1.java)
## Solución
Revisamos el codigo fuente que nos dan
```java
import java.util.*;

  

class VaultDoor1 {

    public static void main(String args[]) {

        VaultDoor1 vaultDoor = new VaultDoor1();

        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter vault password: ");

    String userInput = scanner.next();

    String input = userInput.substring("picoCTF{".length(),userInput.length()-1);

    if (vaultDoor.checkPassword(input)) {

        System.out.println("Access granted.");

    } else {

        System.out.println("Access denied!");

    }

    }

  

    // I came up with a more secure way to check the password without putting

    // the password itself in the source code. I think this is going to be

    // UNHACKABLE!! I hope Dr. Evil agrees...

    //

    // -Minion #8728

    public boolean checkPassword(String password) {

        return password.length() == 32 &&

               password.charAt(0)  == 'd' &&

               password.charAt(29) == '9' &&

               password.charAt(4)  == 'r' &&

               password.charAt(2)  == '5' &&

               password.charAt(23) == 'r' &&

               password.charAt(3)  == 'c' &&

               password.charAt(17) == '4' &&

               password.charAt(1)  == '3' &&

               password.charAt(7)  == 'b' &&

               password.charAt(10) == '_' &&

               password.charAt(5)  == '4' &&

               password.charAt(9)  == '3' &&

               password.charAt(11) == 't' &&

               password.charAt(15) == 'c' &&

               password.charAt(8)  == 'l' &&

               password.charAt(12) == 'H' &&

               password.charAt(20) == 'c' &&

               password.charAt(14) == '_' &&

               password.charAt(6)  == 'm' &&

               password.charAt(24) == '5' &&

               password.charAt(18) == 'r' &&

               password.charAt(13) == '3' &&

               password.charAt(19) == '4' &&

               password.charAt(21) == 'T' &&

               password.charAt(16) == 'H' &&

               password.charAt(27) == '5' &&

               password.charAt(30) == '2' &&

               password.charAt(25) == '_' &&

               password.charAt(22) == '3' &&

               password.charAt(28) == '0' &&

               password.charAt(26) == '7' &&

               password.charAt(31) == 'e';

    }

}
```
Extraemos esta parte del código
```
				password.charAt(00)  == 'd' &&
               password.charAt(29) == '9' &&
               password.charAt(04)  == 'r' &&
               password.charAt(02)  == '5' &&
               password.charAt(23) == 'r' &&
               password.charAt(03)  == 'c' &&
               password.charAt(17) == '4' &&
               password.charAt(01)  == '3' &&
               password.charAt(07)  == 'b' &&
               password.charAt(10) == '_' &&
               password.charAt(05)  == '4' &&
               password.charAt(09)  == '3' &&
               password.charAt(11) == 't' &&
               password.charAt(15) == 'c' &&
               password.charAt(08)  == 'l' &&
               password.charAt(12) == 'H' &&
               password.charAt(20) == 'c' &&
               password.charAt(14) == '_' &&
               password.charAt(06)  == 'm' &&
               password.charAt(24) == '5' &&
               password.charAt(18) == 'r' &&
               password.charAt(13) == '3' &&
               password.charAt(19) == '4' &&
               password.charAt(21) == 'T' &&
               password.charAt(16) == 'H' &&
               password.charAt(27) == '5' &&
               password.charAt(30) == '2' &&
               password.charAt(25) == '_' &&
               password.charAt(22) == '3' &&
               password.charAt(28) == '0' &&
               password.charAt(26) == '7' &&
               password.charAt(31) == 'e';
```

Con este comando lo ordenamos, agarramos la columna 3, quitamos las comillas y los enters
```bash
victormcm-picoctf@webshell:~/reversin$ cat flag | sort | awk '{print($3)}' | tr -d "'" | tr -d "\n"
d35cr4mbl3_tH3_cH4r4cT3r5_75092e;
```
## Notas Adicionales

## Referencias