# Chaining Commands
## Chaining with semicolons
Leant about chaining in the linux terminal, which is highly efficient in the sense that 2 or more commands can be written in the same line and executed together.
for this a ; can be used which works the same way as the enter key does.
for example lets say i want to create a file called cryptonite and then read it
normally I would do:
touch cryptonite
cat cryptonite
but instead to make it better I can just do this
touch cryptonite ; cat cryptonite
which would work the same way.
coming to the question, I was required to run the /challenge/college file and invoke the /challenge/pwn in the same line seperated by a semicolon basically chain those two commands
~~~
bash
/challenge/college ; /challenge/pwn
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{gEddEkVTbtwxii-KNR0xK77lDGa.dVTN4QDL5AjN0czW}
~~~

## Your First Shell Script
In this module I learnt what a shell script is.
Basically a shell script can act as a folder for some complex or very lengthy commands that have been chained together, these commands can be saved in the script and then invoked together when the shell is invoked.
a shell has a suffix .sh and can be created just like a file with the touch command.
in the question I was required to write some commands inside the shell and then invoke it.
but one thing is that I cant write inside a shell normally or with the existing commands which I already know of.
So I had to research a little bit, on how to write inside of a shell as nothing was working and I couldnt solve the question.
the source which I used is -------> https://cloudxlab.com/assessment/displayslide/63/writing-first-shell-script
reading the website, I learnt that the nano command had to be used to write inside of a shell and exit the shell with the key combination Ctrl+X and save the text.
So firstly I created a shell script using the touch command, then nano'd into it and wrote inside of the shell the two commands which were supposed to be written and then used the bash command and got the shell.



~~~
bash
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{IqHyKJiLQsfBn2L29MsyB3DtNrC.dFzN4QDL5AjN0czW}
~~~


## Redirecting Script Output
In this question as well I had to use the nano command to write the commands inside the shell and then pipe the output of the shell inside the solve file.
~~~
bash
hacker@chaining~redirecting-script-output:~$ touch x.sh
hacker@chaining~redirecting-script-output:~$ nano x.sh
hacker@chaining~redirecting-script-output:~$ x.sh | /challenge/solve
ssh-entrypoint: x.sh: command not found
The data piped from /challenge/pwn did not match what I expected. I
re-randomize the data every time you input a new line to the shell, so you must
get it right in one shot! Make sure to pipe the output from your script to
/challenge/solve.
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{U6aDJ-TfkiddMRkRp5qDNyWn4hC.dhTM5QDL5AjN0czW}
~~~

## Executable Shell Scripts
In this question, just like the previous few questions I was firstly required to create a shell, then inside the shell I was required to invoke the solve file.
But whats different in this question is that the bash command wasnt required.
the bash command is basically a different way of invoking a shell which can also be done by calling it from its explicit relative path through the ./ operator.
so here it had to be invoked using the ./ operator.
But here the file also had to be made exectuable firstly using the chmod command to change the permissions of the file.
As done earlier the chmod 700 command could be used here to make it invokable, so I did just that and obtained the flag.
~~~
bash
hacker@chaining~executable-shell-scripts:~$ touch shell.sh
hacker@chaining~executable-shell-scripts:~$ nano shell.sh
hacker@chaining~executable-shell-scripts:~$ ./shell.sh
ssh-entrypoint: ./shell.sh: Permission denied
hacker@chaining~executable-shell-scripts:~$ chmod 700 shell.sh
hacker@chaining~executable-shell-scripts:~$ ./shell.sh
Congratulations on your shell script execution! Your flag:
pwn.college{cRIRagyOfcEgmh27DMH0SXww813.dRzNyUDL5AjN0czW}
~~~
