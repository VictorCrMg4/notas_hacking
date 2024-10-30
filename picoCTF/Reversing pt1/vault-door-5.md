## Objetivo
In the last challenge, you mastered octal (base 8), decimal (base 10), and hexadecimal (base 16) numbers, but this vault door uses a different change of base as well as URL encoding! The source code for this vault is here: [VaultDoor5.java](https://jupiter.challenges.picoctf.org/static/9505cca05dc00fecead41106370ee619/VaultDoor5.java)
## Solución
Nos dan este código.
```java
import java.net.URLDecoder;

import java.util.*;

  

class VaultDoor5 {

    public static void main(String args[]) {

        VaultDoor5 vaultDoor = new VaultDoor5();

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

  

    // Minion #7781 used base 8 and base 16, but this is base 64, which is

    // like... eight times stronger, right? Riiigghtt? Well that's what my twin

    // brother Minion #2415 says, anyway.

    //

    // -Minion #2414

    public String base64Encode(byte[] input) {

        return Base64.getEncoder().encodeToString(input);

    }

  

    // URL encoding is meant for web pages, so any double agent spies who steal

    // our source code will think this is a web site or something, defintely not

    // vault door! Oh wait, should I have not said that in a source code

    // comment?

    //

    // -Minion #2415

    public String urlEncode(byte[] input) {

        StringBuffer buf = new StringBuffer();

        for (int i=0; i<input.length; i++) {

            buf.append(String.format("%%%2x", input[i]));

        }

        return buf.toString();

    }

  

    public boolean checkPassword(String password) {

        String urlEncoded = urlEncode(password.getBytes());

        String base64Encoded = base64Encode(urlEncoded.getBytes());

        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"

                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"

                        + "JTM0JTVmJTM4JTM0JTY2JTY0JTM1JTMwJTM5JTM1";

        return base64Encoded.equals(expected);

    }

}
```

Hacemos lo contrario de lo que hace el codigo
Un URL decode y despues un base 64 decode a exxpected.
![[Pasted image 20241027230406.png]]

c0nv3rt1ng_fr0m_ba5e_64_84fd5095

## Con javascript
```javascript
cad = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVmJTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2JTM0JTVmJTM4JTM0JTY2JTY0JTM1JTMwJTM5JTM1";
cad = atob(cad)
cad = decodeURI(cad)


'c0nv3rt1ng_fr0m_ba5e_64_84fd5095'
```

## Notas Adicionales

## Referencias
https://www.w3schools.com/tags/ref_urlencode.ASP