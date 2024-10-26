# Becoming root with su
```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{oNKFxRWiIQbmPsVsA_9kDg5yxR8.dVTN0UDL0gTN0czW}
```

# Other User with su
```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{8tFVVqLSwWNlvp827lPE5aKx6OV.dZTN0UDL2kjN0czW}
```

# Cracking passwords
```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:03 40% 1/3 0g/s 290.9p/s 290.9c/s 290.9C/s .zardus99999..Mrzardus
0g 0:00:00:15 0% 2/3 0g/s 288.1p/s 288.1c/s 288.1C/s grumpy..keeper
0g 0:00:00:16 0% 2/3 0g/s 288.3p/s 288.3c/s 288.3C/s rockie..surfing
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04960g/s 288.8p/s 288.8c/s 288.8C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ --show
ssh-entrypoint: --show: command not found
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ .challenge/run
bash: .challenge/run: No such file or directory
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{AruIk471Tgu4z8pJSqIdmBaAwpc.ddTN0UDL2kjN0czW}
```

# Using sudo
```
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{UYMbT0WT2KmrJBgpHMQUdFutdUk.dhTN0UDL0gTN0czW}
```
