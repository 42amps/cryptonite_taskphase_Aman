# vault-door-3
Ths challenge was a bit trickier than the previous one.

When you look at the source code, you'll notice that the password is hidden using a bunch of for loops.
It took a bit of analysis, but here’s what I found out:
    1. The first 8 characters of buffer are exactly the same as the first 8 characters of password.
    2. The next block of 8 characters (positions 8 to 15) are placed in reverse order in buffer.
    3. For even indices from 16 to 30, `buffer[i] = password.charAt(46 - i)`.
    4. For odd indices, moving backward from 31 to 17, `buffer[i]` just takes the characters directly from password.

With this pattern figured out, I wrote a simple script to reverse-engineer the password and print it out:
```
public class VaultDoor3Solver {
    public static void main(String[] args) {
        char[] target = "jU5t_a_sna_3lpm18gb41_u_4_mfr340".toCharArray();
        char[] password = new char[32];

        // Reconstruct the password based on the logic in the source code
        int i;
        for (i = 0; i < 8; i++) {
            password[i] = target[i];
        }
        for (; i < 16; i++) {
            password[23 - i] = target[i];
        }
        for (i = 16; i < 32; i += 2) {
            password[46 - i] = target[i];
        }
        for (i = 31; i >= 17; i -= 2) {
            password[i] = target[i];
        }

        System.out.println("picoCTF{" + new String(password) + "}");
    }
}
```
__Flag__:`picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_1fb380}`

![image](https://github.com/user-attachments/assets/64168075-724e-4ef4-b457-3d647c883c62)
