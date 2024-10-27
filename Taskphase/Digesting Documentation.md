# Learning from Documentation
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{4Oh15mjGOmk0DyDZurPBYGskiYr.dRjM5QDL5MTM1czW}
```
# Learning Complex Usage
```
hacker@man~learning-complex-usage:/$ /challenge/challenge --printfile flag
Correct argument! Here is the flag file:
pwn.college{UDxpg-oZ9V2mjGOmk0Dya3BpfHoXr9.dVjM5QDL5MTM1czW}
```
# Reading Manuals
```
hacker@man~reading-manuals:~$ man challenge
DESCRIPTION
       Output the flag when called with the right arguments.
       --fortune
              read a fortune
       --version
              output version information and exit
       --wubwbd NUM
              print the flag if NUM is 264
hacker@man~reading-manuals:~$ /challenge/challenge --wubwbd 264
Correct usage! Your flag: pwn.college{wCTuTYDb2wAMLbLdolfZS6tLGch.dRTM4QDL2kjN0czW}
```
# Searching Manuals
```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$
hacker@man~searching-manuals:~$ /challenge/challenge  --bqag
Initializing...
Correct usage! Your flag: pwn.college{8Z5pW1y-QEqmkRhaurcjMrv4ODc.dVTM4QDL2kjN0czW}
```
# Searching for manuals
```
hacker@man~searching-for-manuals:~$ man man
MAN(1)                Manual pager utils                MAN(1)

NAME
       man - an interface to the system reference manuals

SYNOPSIS
       man [man options] [[section] page ...] ...
       man -k [apropos options] regexp ...
       man -K [man options] [section] term ...
       man -f [whatis options] page ...
       man -l [man options] file ...
       man -w|-W [man options] page ...

DESCRIPTION
       man  is  the system's manual pager.  Each page argument
hacker@man~searching-for-manuals:~$  man -k /challenge/challenge
wdoyaddaqi (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man wdoyaddaqi

CHALLENGE(1)                                            Challenge Commands                                           CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --wdoyad NUM
              print the flag if NUM is 900

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                  May 2024                                                CHALLENGE(1)
hacker@man~searching-for-manuals:~$ /challenge/challenge --wdoyad 900
Correct usage! Your flag: pwn.college{4LCulJDkM-7DQGPi7vYPrGX6jg6.ddjM4QDL2kjN0czW}
```
# Helpful Programs
```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 477
hacker@man~helpful-programs:~$ /challenge/challenge -g 477
Correct usage! Your flag: pwn.college{UsoKu6GBZur53Y9MJ--zyH0kbvZ.ddjM4QDL5MTM1czW}
```
# Help for Builtins
```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune		display a fortune
      --version		display the version
      --secret VALUE	prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "ugjjASxt".
hacker@man~help-for-builtins:~$ challenge --fortune
Some rise by sin and some by virtue fall.
hacker@man~help-for-builtins:~$ challenge --secret ugjjASxt
Correct! Here is your flag!
pwn.college{wCTuTYDb2wAMLbLdolfZS6tLGch.dRTM4QDL2kjN0czW}
```
