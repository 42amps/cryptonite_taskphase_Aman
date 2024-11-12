# ARM Assembly 0:
Solved this by compiling assembly.
Commands to cross compile the challenge ARM Assembly code:
```
aarch64-linux-gnu-as -o chall.o chall.S
aarch64-linux-gnu-gcc -static -o chall chall.o
```
Installing a version of QEMU that runs statically in the background with `sudo apt install qemu-user-static` so we can run ARM binaries like normal programs

Finally we can run the challenge binary with the given arguments:
`./chall 266134863 1592237099`

![image](https://github.com/user-attachments/assets/3385af1a-0cca-48f3-89f8-6aa1b8be1694)

Now using online tool to convert our decimal number to hexadecimal

__Flag__: `picoCTF{5EE79C2B}`
