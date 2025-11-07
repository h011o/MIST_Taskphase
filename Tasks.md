# 1. interencdec

> Can you get the real meaning from this file.
Download the file [here](https://github.com/h011o/madhav_phase2/blob/main/files/enc_flag).

## Solution:

* To start off, I catted the attached file. 

```
 cat enc_flag
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzJhMnd6TW1zeWZRPT0nCg==
```

Looking at the tags, I get the hint that the challenge probably consists of `caesar` and `base64` ciphers. 
<img width="805" height="60" alt="image" src="https://github.com/user-attachments/assets/6b4301f8-ad51-442a-a8c7-c026c7d19436" />


On using a base64 decoder, I get the following output: 

`b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg2a2wzMmsyfQ=='`

I tried this on caesar to get no proper output. I then realized how there was single quotes at the start and end of the base64 deciphered text. On trying base64 again:

`wpjvJAM{jhlzhy_k3jy9wa3k_86kl32k2}`

This is of the standard picoctf flag-format. Now, on trying caesar cipher I got the flag.


## Flag:

```
	picoCTF{caesar_d3cr9pt3d_86de32d2}
```

## Concepts learnt:

I was curious on how the ciphers worked so I took a look.

- `caesar` works by shifting the letters in the plaintext message by a certain number of positions, known as the "shift" or "key". This means `ROT13` is actually a specific type of caesar cipher (13 shifts). 
- `base64` isnt really a cipher, since there is no key. It usually ends with `=` at the end and has many uppercase and lowercase characters.
- It works by splitting binary data into 6 chunks 

## Notes:

-  Wasn't able to identify the initial cipher to be in base64 format.

## Resources:

- https://www.dcode.fr/caesar-cipher
- https://www.dcode.fr/base-64-encoding

***

# Linux Luminarium 

> Hello Hackers

# Challenges
1. Intro To Commands
2. Intro to Arguments
3. Command History
   
# 1. Intro to Commands
This challenge asks you to invoke the hello command to get the flag.

## My solve
**Flag:** `pwn.college{cJN2__KOOkXeKU38nVt-B5hT-QD.QX3YjM1wSM5kjNzEzW}`
```bash
hacker@hello~intro-to-commands:~$ whoami
hacker
hacker@hello~intro-to-commands:~$ Hello
bash: Hello: command not found
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{cJN2__KOOkXeKU38nVt-B5hT-QD.QX3YjM1wSM5kjNzEzW}
```

## What I learned 
I learnt how the promt for the linux terminal is written as **username@hostname:~$**, where the $ symbol means that the user does not have administrative privileges whereas the # symbol means the user is an administrator. I also learnt how linux is case sensitive which means Hello does not provide the same output as hello does.

## References 
None

# 2. Intro to Arguments
This challenge requires you to use the hello command with an argument.
## My solve
**Flag:** `pwn.college{UUwUeA_68O6TltOKivTFhM1-4cV.QX4YjM1wSM5kjNzEzW}`
``` bash 
hacker@hello~intro-to-arguments:~$ echo Hello
Hello
hacker@hello~intro-to-arguments:~$ hello
It looks like you've invoked this command without an argument. Please invoke 
this with a single argument of 'hackers'!
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{UUwUeA_68O6TltOKivTFhM1-4cV.QX4YjM1wSM5kjNzEzW}
```

## What I learned 
I learnt about the echo command which functions similar to the print statement, the way it can input multiple arguments and output them in the terminal.

# 3.  Command History
This challenge requires you to use the command history feautre to retrieve the flag from the memory of the terminal.

## My solve
**Flag:** `pwn.college{83_2T5ZDt_PtgxygGWBnp2dmb8n.0lNzEzNxwSM5kjNzEzW}`
``` bash
hacker@hello~command-history:~$ the flag is pwn.college{83_2T5ZDt_PtgxygGWBnp2dmb8n.0lNzEzNxwSM5kjNzEzW}
```

## What I learned
I learnt how using the arrow keys, we can easily get past commands used in the terminal, which makes it really useful in situations with repetitive commands.

## References 
None

> Pondering Paths

# Challenges
1. The Root
2. Program and absolute paths
3. Position thy self
4. Position elsewhere
5. Position yet elsewhere
6. Implicit relative paths, from /
7. Explicit relative paths, from /
8. Implictive relative path
9. Home sweet home


# 1. The Root
This challenge asks us to invoke the pwn program using its absolute path.

## My solve
**Flag:** `pwn.college{UpHmnW3qBDDvS1AqhTOTVzmLbaw.QX4cTO0wSM5kjNzEzW}`

```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{UpHmnW3qBDDvS1AqhTOTVzmLbaw.QX4cTO0wSM5kjNzEzW}
```

## What I learned
I learned about the tree-like structure of the linux file system, which originates at the root (/), and how we can refer to any file in the linux filesystem by using its *path* that describes the exact location of the file.

## References 
None

# 2. Program and absoulte paths
This challenge asks us to invoke the run program inside the challenge directory

## My solve
**Flag:** `pwn.college{gGA-Ao15J4vKckwqHRgLhAZdJtH.QX1QTN0wSM5kjNzEzW}`

```bash
hacker@paths~program-and-absolute-paths:~$ /
bash: /: Is a directory
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{gGA-Ao15J4vKckwqHRgLhAZdJtH.QX1QTN0wSM5kjNzEzW}
```

## What I learned
I understood that the root (/) itself is a directory and the deeper into the "tree" the file lies, the longer its path becomes because the number of directories increase.

## References 
None

# 3. Position thy self
This challenge asks us to execute a certain program from a specific path.

## My solve
**Flag:** `pwn.college{AK2UsF7F5Z1PwiwlBeE9c2x8ntO.QX2QTN0wSM5kjNzEzW}`

first I located the position of the present directory using (~) after which I tried to run the program which gave me its directory. Then I attempted to change the directory and run the challenge program.

```bash
bash: /home/hacker: Is a directory
hacker@paths~position-thy-self:~$ cd /challenge/run
bash: cd: /challenge/run: Not a directory
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/zoneinfo/posix/Asia directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /usr/share/zoneinfo/posix/Asia/challenge/run
bash: cd: /usr/share/zoneinfo/posix/Asia/challenge/run: No such file or directory
hacker@paths~position-thy-self:~$ cd /usr/share/zoneinfo/posix/Asia
hacker@paths~position-thy-self:/usr/share/zoneinfo/posix/Asia$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{AK2UsF7F5Z1PwiwlBeE9c2x8ntO.QX2QTN0wSM5kjNzEzW}
```

## What I learned
I realized that programs cannot be executed directly from their path before accessing its directory.

## References 
None

# 4. Position elsewhere
This challenge asks us to execute a certain program from a specific path.

## My solve
**Flag:** `pwn.college{g66T1dhFkpzstRbdTFbR-MzoOwD.QX3QTN0wSM5kjNzEzW}`

This flag was obtained following the same process as the previous one.
first I located the position of the present directory using (~) after which I attempted to change the directory and run the challenge program.

```bash
hacker@paths~position-elsewhere:~$ ~
bash: /home/hacker: Is a directory
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /home directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /home
hacker@paths~position-elsewhere:/home$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{g66T1dhFkpzstRbdTFbR-MzoOwD.QX3QTN0wSM5kjNzEzW}
```

## References 
None

# 5. Position yet Elsewhere 
This challenge asks us to execute a certain program from a specific path.

## My solve
**Flag:** `
pwn.college{YTEOjchtbSPJn0jP0_2WWdqL24W.QX4QTN0wSM5kjNzEzW}`

This flag was obtained following the same process as the previous two.
first I located the position of the present directory using (~) after which I attempted to change the directory and run the challenge program.

```bash
hacker@paths~position-yet-elsewhere:~$ ~
bash: /home/hacker: Is a directory
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /proc/138/fd directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /proc/138/fd
hacker@paths~position-yet-elsewhere:/proc/138/fd$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{YTEOjchtbSPJn0jP0_2WWdqL24W.QX4QTN0wSM5kjNzEzW}
```

## What I learned
I understood the concept of the 'cd' command in navigating the linux filesystem.

## References 
None

# 6. Implicit relative paths, from /
This challenge asks us to execute a certain program using a relative path.  

## My solve
**Flag:** `
pwn.college{sA_F56BVy74uMxPUlSWHq6QyY0e.QX5QTN0wSM5kjNzEzW}`


```bash
hacker@paths~implicit-relative-paths-from-:~$ ~
bash: /home/hacker: Is a directory
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{sA_F56BVy74uMxPUlSWHq6QyY0e.QX5QTN0wSM5kjNzEzW}
```

## What I learned
I understood the concept of a relative path which refers to the relative position of a file with respect to the directory it is under. Relative paths are used to navigate directories based on your current location in the file system whereas an absolute path is used to navigate directly to a specific directory from the root, regardless of your current location.

## References 
https://www.geeksforgeeks.org/linux-unix/absolute-relative-pathnames-unix/



# 7. Explicit relative paths, from /
This challenge requires us to use the . operator inside the / directory to get our flag.


## My solve
**Flag:** `
pwn.college{sA_F56BVy74uMxPUlSWHq6QyY0e.QX5QTN0wSM5kjNzEzW}  `


```bash
hacker@paths~explicit-relative-paths-from-:~$ ~
bash: /home/hacker: Is a directory
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/./run
Correct!!!
./challenge/./run is a relative path, invoked from the right directory!
Here is your flag:
```

## What I learned
I noticed how the explicit relative path is a more precise way of looking for programs inside a directory.

## References 
None

# 8. Implictive relative path
This challenge asks us to use . operator inside the /challenge directory to get our flag.

## My solve
**Flag:** `pwn.college{4UUZA06Vfd65dJaa-2r1NkpvzL8.QXxUTN0wSM5kjNzEzW}`

```bash
hacker@paths~implicit-relative-path:~$ ~
bash: /home/hacker: Is a directory
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ /run
bash: /run: Is a directory
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{4UUZA06Vfd65dJaa-2r1NkpvzL8.QXxUTN0wSM5kjNzEzW}
```

## What I learned
I learnt how the linux filesystem automatically avoids looking in the current directory when a naked path is provided to prevent accidental execution of programs. This is where the importance of explicit path lies, it *explicitly* tells the Linux filesystem to execute the program in the current directory

## References 
None

# 9. Home sweet home
This challenge requires us to copy the flag to /home/hacker under a set of three constraints.
Your argument must be an absolute path.
The path must be inside your home directory.
Before expansion, your argument must be three characters or less.

## My solve
**Flag:** `pwn.college{AdlOEI47qeSdsoecuITXvu7CGkT.QXzMDO0wSM5kjNzEzW} `

Firstly, the path had to be absolute. So I started the file path with (/) which was already one character. Then, I used the (~) which represented the home directory for the challenge path to write a copy of the flag to the file named 'm'.

```bash
hacker@paths~home-sweet-home:/$ challenge/run
You must provide an argument to /challenge/run when you invoke it!
hacker@paths~home-sweet-home:/$ challenge/run ~/m
Writing the file to /home/hacker/m!
... and reading it back to you:
pwn.college{AdlOEI47qeSdsoecuITXvu7CGkT.QXzMDO0wSM5kjNzEzW}

```

## What I learned.
I learnt that files can be transferred from a different directory to the home directory using the (~) operator

## References 
None











