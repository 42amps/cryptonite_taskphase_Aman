# vault-door-5

__Flag__:`picoCTF{c0nv3rt1ng_fr0m_ba5e_64_e3152bf4}`

In this the password string undergoes a two step encoding process:
- URL Encoding: The password is first URL encoded. It converts characters into format that can be transmitted over the internet. Each byte is represented by a percentage `%` followed by two hexadecimal digits.
- Base 64 Encoding: After the URL encoding, the resulting string is then base64-encoded.

Now to solve this, we need to reverse the encoding steps:
- First we need to decode the expected string from base64.
- After that we need to URL-decode the resulting string from the base64 decode.

Here's a script that does the job.
```java
import java.net.URLDecoder;
import java.util.Base64;

public class Main {  
    public static void main(String[] args) {
        try {
            String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                            + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                            + "JTM0JTVmJTY1JTMzJTMxJTM1JTMyJTYyJTY2JTM0";

            // Step 1: Base64 decode
            byte[] base64Decoded = Base64.getDecoder().decode(expected);

            String urlDecoded = new String(base64Decoded);
            String decodedPassword = URLDecoder.decode(urlDecoded, "UTF-8");

            System.out.println("Decoded password: " + decodedPassword);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

![image](https://github.com/user-attachments/assets/20e00f30-08f4-4738-868e-cf29c90ba212)
