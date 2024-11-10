# vault-door-1
This was fairly straight forward since all we had to do was rearrange the characters with their respective indexes.
We can do it manually or we can write a script which will do it for us.

__Flag__: `picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_ff63b0}`

```
public class PasswordSolver {
    public static void main(String[] args) {
        // Initialize an array of length 32 (since the password length is 32)
        char[] password = new char[32];

        // Set the characters at their respective positions as per the checkPassword method
        password[0]  = 'd';
        password[1]  = '3';
        password[2]  = '5';
        password[3]  = 'c';
        password[4]  = 'r';
        password[5]  = '4';
        password[6]  = 'm';
        password[7]  = 'b';
        password[8]  = 'l';
        password[9]  = '3';
        password[10] = '_';
        password[11] = 't';
        password[12] = 'H';
        password[13] = '3';
        password[14] = '_';
        password[15] = 'c';
        password[16] = 'H';
        password[17] = '4';
        password[18] = 'r';
        password[19] = '4';
        password[20] = 'c';
        password[21] = 'T';
        password[22] = '3';
        password[23] = 'r';
        password[24] = '5';
        password[25] = '_';
        password[26] = 'f';
        password[27] = 'f';
        password[28] = '6';
        password[29] = '3';
        password[30] = 'b';
        password[31] = '0';

        // Convert the array to a string and print it
        String solvedPassword = new String(password);
        System.out.println("The solved password is: picoCTF{" + solvedPassword + "}");
    }
}
```

![image](https://github.com/user-attachments/assets/1ee59163-a491-4732-bd70-6fde8c1acdc9)
