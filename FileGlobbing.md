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

