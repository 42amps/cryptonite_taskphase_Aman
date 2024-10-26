# Module 3
This module introduces us to some useful linux commands which will help us in understanding the linux file system.

## Challenges:
# cat: not the pet, but the command

```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{8N7R75zxoE1V0aStrDyaX0mq2o-.dFzN1QDL2kjN0czW}
```
Learned about the cat command which reads out the content of any file.

# catting absolute paths
In this, we just read the contents by giving the absolute path of the file i.e. /flag

``` 
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{IW8G7nmgjoLdaqd-W_6C5d-vsNP.dlTM5QDL0gTN0czW}
```
# more catting practice

``` 
Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /usr/lib/pkgconfig/flag. Go cat it out **without** cding into that
directory!
hacker@commands~more-catting-practice:~$ cat /usr/lib/pkgconfig/flag
pwn.college{8_bwSJvoISl5BAaukCyBjRja6e3.dBjM5QDL0gTN0czW}

```
# grepping for a needle in a haystack
When the file content is too large, we can use grep to search for a specific string using arguemnt.

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{gwQWp2ms0r9COVVTJLlSRKu2o1S.ddTM4QDL2kjN0czW}
```

# listing files
ls is a command used to listing files in a directory.

```
hacker@commands~listing-files:~$ ls /challenge
27802-renamed-run-6901  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/27802-renamed-run-6901
Yahaha, you found me! Here is your flag:
pwn.college{IMPE55WpRRmSF0xk4nGcaLZzZmh.dhjM4QDL0gTN0czW}
```
# touching files
touch command is used to create a new file

```
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{YOs7bq7BTDO55sHieirBdz7k3-z.dBzM4QDL2kjN0czW}
```
# removing files
rm command is used to remove files

```
hacker@commands~removing-files:~$ ls
Desktop  delete_me  j
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ ls
Desktop  j
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{8hAijCG33_lFf41Z9hlaPkMm4pZ.dZTOwUDL0gTN0czW}
```

# hidden files
Some files cannot be seen when we use ls command, so ls -a shows all the files including files starting with .file_name

```
hacker@commands~hidden-files:~$ ls -a /
.                      bin        etc    lib64   nix   run   tmp
..                     boot       home   libx32  opt   sbin  usr
.dockerenv             challenge  lib    media   proc  srv   var
.flag-146782335826902  dev        lib32  mnt     root  sys
hacker@commands~hidden-files:~$ /.flag-146782335826902
ssh-entrypoint: /.flag-146782335826902: Permission denied
hacker@commands~hidden-files:~$ cat /.flag-146782335826902
pwn.college{ktDm3goSkCtPdeRh0i5Nfn9y-xE.dBTN4QDL0gTN0czW}
```

# An Epid Filesystem Quest

In this question I had problem in reading the file but without cd'ing into the directory.
However after some attempts I figured it out.

```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
TIP  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin  challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat TIP
Tubular find!
The next clue is in: /usr/share/racket/pkgs/distributed-places-doc/scribblings/distributed-places

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/$ ls -a /usr/share/racket/pkgs/distributed-places-doc/scribblings/distributed-places
.  ..  .BRIEF  compiled  distributed-places.scrbl  info.rkt  rmpi.scrbl
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/share/racket/pkgs/distributed-places-doc/scribblings/distributed-places/.BRIEF
Great sleuthing!
The next clue is in: /usr/lib/R/library/splines/R

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/lib/R/library/splines/R
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/splines/R$ ls -a
.  ..  .INFO  splines  splines.rdb  splines.rdx
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/splines/R$ cat .INFO
Tubular find!
The next clue is in: /opt/rappel/.git/objects/f7

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/splines/R$ ls -a /opt/rappel/.git/objects/f7
.  ..  9809bcb70ce88c1f9f355970e01c23f6116353  NOTE-TRAPPED
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/splines/R$ cat /opt/rappel/.git/objects/f7/NOTE-TRAPPED
Great sleuthing!
The next clue is in: /usr/local/share/doc/networkx-3.1/examples/3d_drawing/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/splines/R$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls -a  /usr/local/share/doc/networkx-3.1/examples/3d_drawing/__pycache__
.  ..  BLUEPRINT  mayavi2_spring.cpython-38.pyc  plot_basic.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/$ cat  /usr/local/share/doc/networkx-3.1/examples/3d_drawing/__pycache__/BLUEP
RINT
Lucky listing!
The next clue is in: /opt/radare2/shlr/capstone/msvc/test_arm

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/radare2/shlr/capstone/msvc/test_arm
NUGGET-TRAPPED  test_arm.vcxproj
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/radare2/shlr/capstone/msvc/test_arm/NUGGET-TRAPPED
Lucky listing!
The next clue is in: /usr/lib/R/library/translations/fr/LC_MESSAGES
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/lib/R/library/translations/fr/LC_MESSAGES
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/translations/fr/LC_MESSAGES$ ls -a
.        R-base.mo       R-graphics.mo  R-parallel.mo  R-stats4.mo  R-utils.mo  grDevices.mo  methods.mo   stats.mo
..       R-compiler.mo   R-grid.mo      R-splines.mo   R-tcltk.mo   R.mo        graphics.mo   parallel.mo  tcltk.mo
INSIGHT  R-grDevices.mo  R-methods.mo   R-stats.mo     R-tools.mo   RGui.mo     grid.mo       splines.mo   tools.mo
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/translations/fr/LC_MESSAGES$ cat INSIGHT
Great sleuthing!
The next clue is in: /usr/share/nvim/runtime/autoload/dist

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/translations/fr/LC_MESSAGES$ cd  /usr/share/nvim/runtime/autoload/dist
hacker@commands~an-epic-filesystem-quest:/usr/share/nvim/runtime/autoload/dist$ ls
POINTER  ft.vim
hacker@commands~an-epic-filesystem-quest:/usr/share/nvim/runtime/autoload/dist$ cat POINTER
Yahaha, you found me!
The next clue is in: /usr/share/rubygems-integration/all/specifications

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/nvim/runtime/autoload/dist$ cd /usr/share/rubygems-integration/all/specifications
hacker@commands~an-epic-filesystem-quest:/usr/share/rubygems-integration/all/specifications$ ls
README                   net-telnet-0.1.1.gemspec    rake-13.0.1.gemspec      xmlrpc-0.3.0.gemspec
minitest-5.13.0.gemspec  power_assert-1.1.7.gemspec  test-unit-3.3.5.gemspec

hacker@commands~an-epic-filesystem-quest:/usr/share/rubygems-integration/all/specifications$ cat README
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{AnVgcIctpbmmXONKvqi-pMKr-3h.dljM4QDL0gTN0czW}
```

# making directories
```
hacker@commands~making-directories:/$ cd /tmp
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{URwFKppOSZVQ_PWL2ydiTLOsobN.dFzM4QDL0gTN0czW}
```

# finding files
```
hacker@commands~finding-files:~$ cat /usr/share/racket/pkgs/plot-lib/plot/flag
pwn.college{c87NNUb4oc6BLGLbwr93d1LXpzH.dJzM4QDL2kjN0czW}
```

# Linking files
```
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{8x8VuEA-kUpaSi8G5eXAvflpqNP.dlTM1UDL0gTN0czW}
```
