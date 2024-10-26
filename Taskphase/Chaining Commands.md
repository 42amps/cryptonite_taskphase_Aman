# Challengs:
# Chaining with Semicolons
semicolons are used to chain commands we just have to separate each execution using semicolon.

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{EIV1hOMa3AcLmlEmj-R7qAFQfaz.dVTN4QDL2kjN0czW}
```

# Your First Shell Script
In this, we created our first shell script which ends with .sh suffix
```
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ echo "/challenge/pwn ; /challenge/college" > x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{Q89JT6wgbhWk60QVd4-zwTx9NdJ.dFzN4QDL0gTN0czW}
```

# Redirecting Script Output
Same as previous challenge, we first store the commands in a file of .xh format and redirect the script output using piping
```
hacker@chaining~redirecting-script-output:~$ echo /challenge/pwn > x.sh
hacker@chaining~redirecting-script-output:~$ echo /challenge/college >> x.sh
hacker@chaining~redirecting-script-output:~$ chmod +x x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{oAM51RzDPE-60VSeWCDt2thZBD9.dhTM5QDL2kjN0czW}
```
# Executable Shell Scripts
In this we first store the commands in a file script.sh then change its permissions in order to execute the file.
 I used chmod+x to make the script executable and then ran it in the terminal to get the flag.
 ```
hacker@chaining~executable-shell-scripts:~$ echo "/challenge/solve" > script.sh
hacker@chaining~executable-shell-scripts:~$ ls -l script.sh
-rw-r--r-- 1 hacker hacker 17 Oct 17 05:43 script.sh
hacker@chaining~executable-shell-scripts:~$ chmod ugo+x ~/script.sh
hacker@chaining~executable-shell-scripts:~$ ./script.sh
Congratulations on your shell script execution! Your flag:
pwn.college{sN_kGXJnSt2Qpxvdr6_uGFfJsY0.dRzNyUDL0gTN0czW}
```
