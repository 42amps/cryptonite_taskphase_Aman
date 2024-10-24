# Module 2
In this module, We get to learn about the basics of Linux filesystem and it has been compared to a tree
because it has a root (written as /)

All the filesystems start with /. Under which we can access subsequent directories leading us to their 
respective files and programs.

Learnings throughout the Module
* `.` refers to the same directory
* `..` refers to the parent directory

## The Root
In this challenge, we have been given a program 'pwn' that will give us the flag when invoked
`pwn.college{UCRYmXWN1TZFKhHcj8hDBTATUVD.dhzN5QDL1QjN1czW}`

## Program and absolute paths
Our task is the same as before but the file that contains our flag comes under a different directory than before
`pwn.college{EgwepQBmeAGqPF0Chb3XKjURwXu.dVDN1QDL1QjN1czW}`

## Position thy self 
In this we have been introduced to the command 'cd' (change directory) to navigate around directories
This affects the current working directory.
When /challenge/run has been invoked, it gives us the following error

![image](https://github.com/user-attachments/assets/30ac0f09-9685-4863-8132-a90e04508bb4)

We get the flag when we travel to that directory and invoke the 'run' program again

`pwn.college{cyuazGxqfWqlOhVdg6iDnudjxyP.dZDN1QDL1QjN1czW}`

## Position elsewhere
Same as before

`pwn.college{wq8yt95yO3RxC-mpEOGeE1W1Lnt.ddDN1QDL1QjN1czW}`

## Position yet elsewhere
Again the same as before

`pwn.college{8jf980cq4SIkMlrPo9G25dcF4KE.dhDN1QDL1QjN1czW}`

## implicit relative paths, from /

![image](https://github.com/user-attachments/assets/7ee9e72c-3787-46cc-a762-00309b2b23ab)

## explicit relative paths, from /

![image](https://github.com/user-attachments/assets/5c6a3088-61fc-43e3-b000-57d26fea1f4c)

While invoking the run program, we first tried to invoke it through an absolute path which in turn gave us an error
therefore we used `.` since `./challenge/run` is a relative path.

`pwn.college{E2tj4lXSsXzKHjM_UGhNB9W3W0f.dBTN1QDL1QjN1czW}`

## implicit relative path
This required us first to go into challenge directory and later using the relative path `./run` to get the flag.

![image](https://github.com/user-attachments/assets/bc130980-b5a5-4eef-b877-0d5b57a13289)

`pwn.college{IviFEFqUxoY98XYgCXy7qEGnaCY.dFTN1QDL1QjN1czW}`

## home sweet home

Since `~` is an absolute path which is expanded to `/home/hacker`
By using `~/f`, `/challenge/run` will write a copy of the flag to the file destination `/home/hacker/f`.

![image](https://github.com/user-attachments/assets/f284d0f5-9f1a-4085-b4df-81e07a455c3a)

`pwn.college{4P7hqsxTDiOitHzOIf6Q7QOwapn.dNzM4QDL1QjN1czW}`


