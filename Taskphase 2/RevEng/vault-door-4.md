# vault-door-4

In this challenge, we had to convert the byte array that was given into characters.

Structure of myBytes Array:
  `myBytes` is a predefined array containing `32` elements. Each element is defined using different numerical bases
  
- Decimal: Values like `106`, `85`, `53`.
- Hexadecimal: Values prefixed with `0x`, e.g., `0x55`, `0x6e`.
- Octal: Values prefixed with a leading zero, e.g., `0142`, `0131`.
- Character literals: `a`, `8`, etc.

Each element in `myBytes` represents a character in the password. By converting each byte to a character, you can reconstruct the password.

Using a simple script:
```java
public class Main {
    public static void main(String[] args) {
        byte[] myBytes = {
            106, 85, 53, 116, 95, 52, 95, 98,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063, 0163, 0137, 0146, 064,
            'a', '8', 'c', 'd', '8', 'f', '7', 'e'
        };

        for (byte b : myBytes) {
            System.out.print((char) b);
        }
        System.out.println();
    }
}
```
Running this script will print the password as a string

__Flag__:`picoCTF{jU5t_4_bUnCh_0f_bYt3s_f4a8cd8f7e}`

![image](https://github.com/user-attachments/assets/bec5ae38-b040-4d48-a7ae-fe29f938252e)
