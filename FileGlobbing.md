# File Globbing
## Matching with *
In this module I learnt about globbing which is a method of finding or invoking files without typing their full names but instead using symbols which act as a wildcard and if they starting or ending letters match some file
it would automatically get invoked. Directories can also be changed with this method.
For example, lets say I create some new files inside the terminal using the touch command
~~~
bash
cd /
touch cryptoniteisfun
echo fun: crypt*
fun: cryptoniteisfun
~~~
as is visible by the above result the * symbol acted as a wildcard and still invoked the program cryptoniteisfun as it matched with the initial letters.
This is what I have to do in this specific question, using the * symbol I have to change my directory to /challenge in lesser than 4 characters.
This can be done with typing /ch* which would change the directory and then simply invoking the run program.
~~~
bash
hacker@globbing~matching-with-:~$ cd /challenge
You specified the path to 'cd' to in more than 4 characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /cha*
You specified the path to 'cd' to in more than 4 characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{EMu0tqXOXutz4OgQ97halij7LAZ.dFjM4QDL5AjN0czW}
~~~
I did some MySQL in my 12th grade and I remember sql also contains a like command which can act as a wildcard in the same exact way the symbols are working here.

## Matching with ?
Well similiar to the above question, this one also had the concept of globbing just with the symbol ? instead of *
also had a different requirement which can be seen in the commands below:
~~~
bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{Yna2FpuusDOJAQPDeehiiWi1gI1.dJjM4QDL5AjN0czW}
~~~


## Matching with []
This module taught me how to glob with [], like I can place some letters inside the square brackets and it would show the result with the letters matching with those files.
so like the previous modules I did the same here in terms of globbing.
~~~
bash
file_[bash]
ssh-entrypoint: file_a: command not found
hacker@globbing~matching-with-:/challenge/files$ /file_[bash]
ssh-entrypoint: /file_[bash]: No such file or directory
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{A0S46-3PKsg42mNURLzHWdLJozY.dNjM4QDL5AjN0czW}
~~~

## Matching Paths with []
Module taught me how to match paths with [], similar to invoking a program.
File paths can also be reffered to with [].
As the question said I had to invoke /challenge/files through /challenge/run in a simple argument by using square brackets.
So I did that by cding into the home/hacker file as challenge/files wasnt a part of /

~~~
bash
hacker@globbing~matching-paths-with-:~$ cd /
hacker@globbing~matching-paths-with-:/$ /challenge/run /challenge/files/file_[bash]
Error: please run with a working directory of /home/hacker!
hacker@globbing~matching-paths-with-:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@globbing~matching-paths-with-:/$ cd /home/hacker
hacker@globbing~matching-paths-with-:~$ ls
Desktop  catflag  delete_me  e  file1  flag  new  not-the-flag
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{AQqbcxO_oqwhi8nC__hf4YCoGX2.dRjM4QDL5AjN0czW}
~~~

## Mixing Globs
As the module said that I had to invoke three file paths using the [] operator.
first of all I tried to cd'ed into /challenge/files as the module instructed.
then I mistakenly wrote /cep[]* which is of course wrong as cep is a file and not an absolute path.
then i corrected it by just passing [cep]* as it is a file.
The logic I used was that [cep] was for the initial letters of the files that were to be expanded and * was used for the rest of the variable letters. 
~~~
bash
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run/[cep]*
ssh-entrypoint: /challenge/run/[cep]*: Not a directory
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run/[cep]
ssh-entrypoint: /challenge/run/[cep]: Not a directory
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]
Your expansion did not expand to the requested files (challenging, educational,
pwning). Instead, it expanded to:
[cep]
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{QjmOkjO396msv86UCDP8AUALIrq.dVjM4QDL5AjN0czW}
~~~


## Exclusionary globbing
this module was for specifically excluding files in the file search process using globbing which contain some specific letters.
square brackets [] operator is again used for this but here inside [] a ^ or ! has to be placed to exclude files.
for example if there are 2 files already created with the name of kryptfun and kryptis
and I pass the command krypt[!f]* or krypt[^f]* then only kryptis would be displayed as a result because anything that contains the letter f has been excluded.
the challenge instructed me to cd into /challenge/files and then invoke /challenge/run and exclude anything that stars with p, w and n so I did that with [!pwn]* so I did that.
~~~
bash
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{MQiTrn_xkQ7eorD1vAMv0IKwUjK.dZjM4QDL5AjN0czW}
~~~







