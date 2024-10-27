# Matching with *
```
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{EnmiVtyOkvUI_i5jbJ6S8p5GrCr.dJjM4QDL2kjN0czW}
```
# MAtching with ?
```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{0IovPNlYhcdoWpW8eyJBWejfIay.dJjM4QDL5MTM1czW}
```
# Matching with []
```
hacker@globbing~matching-with-:~$ /challenge/files
ssh-entrypoint: /challenge/files: Is a directory
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ ls
file_a  file_c  file_e  file_g  file_i  file_k  file_m  file_o  file_q  file_s  file_u  file_w  file_y
file_b  file_d  file_f  file_h  file_j  file_l  file_n  file_p  file_r  file_t  file_v  file_x  file_z
hacker@globbing~matching-with-:/challenge/files$ cat file_[absh]
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{AY0zbmO9SklfV_j_qJqyL_rgwS_.dNjM4QDL2kjN0czW}
```
# Mixing globs
```
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing      delightful   great       jovial    magical     pwning   splendid   victorious  youthful
beautiful    educational  happy       kind      nice        queenly  thrilling  wonderful   zesty
challenging  fantastic    incredible  laughing  optimistic  radiant  uplifting  xenial
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{wp5Ph1R1K-EtiUrXrrqYl7fI8Pc.dVjM4QDL2kjN0czW}
```
# Exclusionary Globs
```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{Q0XYsLBFDWsyLlRejkoFipNQ0K-.dZjM4QDL5MTM1czW}
```
