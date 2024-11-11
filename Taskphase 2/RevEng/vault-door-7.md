# vault-door-7
__Flag__:`picoCTF{A_b1t_0f_b1t_sh1fTInG_702640db5a}`

In this the password is being checked by first converting the hexadecimal string into an array of 32 bit integers. The password is expected to be 32 characters long.

## What is exactly happening in the code:

- Password Conversion: The password is represented as a hexadecimal string. The method `passwordToIntArray` splits the string into 8 chunks(4 characters each) and converts each chunk into a 32 bit integer. These 8 integers are compared to harcoded values to verify the password.
- Password Check: The password needs to be exactly 32 characters (32 hexadecimal digits). If the input passes this check, its converted to an integer array which is then compared with specific integer values.

Now to decode this, we need to reverse the process by taking the 8 integers and converting them back to their corresponding 4 byte string.

The script that will help us decode this:
```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

class Main {
    public static void main(String args[]) throws IOException {
        int[] x = {
            1096770097,
            1952395366,
            1600270708,
            1601398833,
            1716808014,
            1734293296,
            842413104,
            1684157793
        };

        // Convert these integers back to a hex string
        StringBuilder passwordHex = new StringBuilder();
        for (int i = 0; i < x.length; i++) {
            int value = x[i];
            for (int j = 0; j < 4; j++) {
                passwordHex.append(String.format("%02x", (value >> (24 - j * 8)) & 0xFF));
            }
        }

        // Convert hex string to ASCII string
        String hexString = passwordHex.toString();
        StringBuilder password = new StringBuilder();
        for (int i = 0; i < hexString.length(); i += 2) {
            String hex = hexString.substring(i, i + 2);
            password.append((char) Integer.parseInt(hex, 16));
        }

        System.out.println("Decoded password: " + password.toString());

        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        System.out.print("Enter vault password: ");
        String userInput = reader.readLine();
        
        String input = userInput.substring("picoCTF{".length(), userInput.length() - 1);

        if (input.equals(password.toString())) {
            System.out.println("Access granted.");
        } else {
            System.out.println("Access denied!");
        }
    }
}

```

What's exactly happening in the script:
- Integer to Hex conversion
- Hex to ASCII
- Comparison

![image](https://github.com/user-attachments/assets/248cc666-d3d7-40d1-b5f7-840bb10e9520)
