# Practicing Piping
## Intro
Firstly, at the start of this new module I learnt the meaning of piping which basically means chaining multiple commands together.
More specifically it can be understood as or how I understood it was that it basically refers to input and output redirection.
Then I learnt 3 very important topics namely standard input(the input which one is passing to the terminal which in turn has some kind of consequence on the terminal like chaning directory etc provided its a valid command inside of linux).
Standard Output is the channel or medium through which some output is processed inside of the terminal. ls command is an example to this as it displays all the files.
standard error which is responsible for displaying an error if some command is mistyped then the shell would display an error.
These 3 are also reffered to as their shorter names namely stdin, stdout and stderr.

## Redirecting Output
After learning and processing all the information I went on to the question where the module instructed me to redirect stdout to files, which can be done with the > character.
for example if I want to write some specific data inside a file I can do that by using this symbol.
Lets say I have a file named krypt, then the command echo learning > krypt would be used and then I can read the file krypt by the cat command which would display learning.
So the question simply told me to write this data or if I put it more specifically to redirect the input PWN inside the file COLLEGE.
~~~
bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{YSiG56xJzGB0GghvZH-8ahTId-F.dRjN1QDL5AjN0czW}
~~~
