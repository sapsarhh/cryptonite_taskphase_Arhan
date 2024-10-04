# Practicing Piping
## Intro
Firstly, at the start of this new module I learnt the meaning of piping which basically means chaining multiple commands together.
More specifically it can be understood as or how I understood it was that it basically refers to input and output redirection.
Then I learnt 3 very important topics namely standard input(the input which one is passing to the terminal which in turn has some kind of consequence on the terminal like chaning directory etc provided its a valid command inside of linux).
Standard Output is the channel or medium through which some output is processed inside of the terminal. ls command is an example to this as it displays all the files.
standard error which is responsible for displaying an error if some command is mistyped then the shell would display an error.
These 3 are also reffered to as their shorter names namely stdin, stdout and stderr.
Referred to this video for understanding more ------> https://www.youtube.com/watch?v=zMKacHGuIHI&ab_channel=LearnLinuxTV


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

## Redirecting More Output
Now, I learnt that using the echo command is not necessary to redirect output data from one file to the other, it can be done by using other commands as well.
So in the question I was asked to do this as I had to redirect the data from /challenge/run to myflag and then read the myflag file using the cat command.
~~~
bash
hacker@piping~redirecting-more-output:~$ cat myflag
#!/opt/pwn.college/bash

DIR=$(/bin/dirname ${BASH_SOURCE[0]})
exec $DIR/chio.py --reward /flag --check_stdout_path myflag --chio_hint_fd -1 --chio_flag_fd 1
hacker@piping~redirecting-more-output:~$ cat /challenge/run > myflag
hacker@piping~redirecting-more-output:~$ cat myflag
#!/opt/pwn.college/bash

DIR=$(/bin/dirname ${BASH_SOURCE[0]})
exec $DIR/chio.py --reward /flag --check_stdout_path myflag --chio_hint_fd -1 --chio_flag_fd 1
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{gp-8h4hSqXJHGRtlM2hqrTCdcce.dVjN1QDL5AjN0czW}
~~~
As you can see firstly I tried redirecting the data by using the cat command but that obviously didnt work, frankly I dont know why I tried that but okay.
I mean it is 2 in the morning right now so, anyways onto the next question.


## Appending Output


