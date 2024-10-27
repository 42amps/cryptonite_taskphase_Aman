# Listing Processes
```
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 09:03 ?        00:00:00 /sbin/docker-init -- /nix/va
root           7       1  0 09:03 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 09:03 ?        00:00:00 /challenge/11806-run-19972
root          72      68  0 09:03 ?        00:00:00 sleep 6h
hacker        73       0  0 09:03 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        90      73  0 09:03 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/11806-run-19972
Yahaha, you found me! Here is your flag:
pwn.college{A2JLRR0mYxDk1g9VyYmLMIzm81s.dhzM4QDL1QjN1czW}
Now I will sleep for a while (so that you could find me with 'ps').
```
# Killing processes
```
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 09:05 ?        00:00:00 /sbin/docker-init -- /nix/va
root           7       1  0 09:05 ?        00:00:00 /run/dojo/bin/sleep 6h
root          71       1  0 09:05 ?        00:00:00 su -c /challenge/.launcher h
hacker        73      71  0 09:05 ?        00:00:00 /challenge/dont_run
hacker        74      73  0 09:05 ?        00:00:00 sleep 6h
hacker        75       0  0 09:05 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker       100      75  0 09:07 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ kill 71
ssh-entrypoint: kill: (71) - Operation not permitted
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{4CQOo6CGZd33OGfHsPDTAFdjJFr.dJDN4QDL1QjN1czW}
```
# Interrupting Processes
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{kZ83mk2MWdr-Qjek9IA5-sryC32.dNDN4QDL1QjN1czW}
```
# suspending Processes
```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 09:09 pts/0    00:00:00 bash /challenge/run
root          84      82  0 09:09 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 09:09 pts/0    00:00:00 bash /challenge/run
root          89      65  0 09:10 pts/0    00:00:00 bash /challenge/run
root          91      89  0 09:10 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{E78hA_ZhSYoKBZF42R2P84t7ho4.dVDN4QDL1QjN1czW}
```
# Resuming processes
```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{0YAzUbrUYdqJiPFMvcd7cU6ZoEO.dZDN4QDL1QjN1czW}
Don't forget to press Enter to quit me!

Goodbye!
```
# Backgrounding Processes
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         660 S+   bash /challenge/run
root         662 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         660 S    bash /challenge/run
root         696 S    sleep 6h
root         735 S+   bash /challenge/run
root         737 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{AwLrjP27pFTqwxDUfo5AERQ9FGx.ddDN4QDL0QjN5YzW}
```
# Foregrounding Processes
```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{YFV-zboLf3VbNzNk3JYmqmgqsEb.dhDN4QDL1QjN1czW}
```
# Starting Backgrounded Processes
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 82
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{8wIoWLzWc6f4qtujcTE_3OQ_o5U.dlDN4QDL1QjN1czW}
```
# Process Exit Codes
```
hacker@processes~process-exit-codes:~$ /challenge/get-code $?
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
84
hacker@processes~process-exit-codes:~$ /challenge/submit-code 84
CORRECT! Here is your flag:
pwn.college{kzdVrShnKIHHfDjkl7j1z8byUd5.dljN4UDL1QjN1czW}

```
