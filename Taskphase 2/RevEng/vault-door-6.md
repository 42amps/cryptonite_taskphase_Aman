# vault-door-6
__Flag__:`picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_3ce2919}`

In this the password is encoded using XOR and then checked with a predefined byte array.
The `checkPassword` method uses a `XOR` operation and compares it with the `myBytes` array.

- Each byte of the password is XORed with `0x55`
- Then the result is subtracted by the corresponding value in the `myBytes` array.
- If the result is not zero for any byte, the password is considered inavalid

Now to decode this, we need to reverse the process:
- Reverse the subtraction by adding the `myBytes` value.
- Reverse the XOR operation by XORing the result with `0x55`.

Here is a script that does the job for us:
```
import java.util.*;

class Main {  // Class name should be capitalized (Main)
    public static void main(String args[]) {
        // The predefined byte array 'myBytes'
        byte[] myBytes = {
            0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
            0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
            0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
            0xa , 0x66, 0x36, 0x30, 0x67, 0x6c, 0x64, 0x6c,
        };

        // The XOR value used during encoding
        byte xorValue = 0x55;

        // Create a StringBuilder to store the decoded password
        StringBuilder decodedPassword = new StringBuilder();

        // Decode each byte in the 'myBytes' array
        for (int i = 0; i < myBytes.length; i++) {
            // Reverse the XOR operation (XOR with 0x55)
            byte decodedByte = (byte) (myBytes[i] ^ xorValue);
            decodedPassword.append((char) decodedByte);  // Convert the byte to char
        }

        // Print the decoded password
        System.out.println("Decoded password: " + decodedPassword.toString());
    }
}
```

![image](https://github.com/user-attachments/assets/ad97da98-cfbf-4017-9a03-a021cb4ac8f5)
