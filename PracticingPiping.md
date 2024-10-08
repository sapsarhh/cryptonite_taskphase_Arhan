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
In this submodule I learnt how to append(add) some text into a file which already has some data inside it.
Appending can be done with the >> symbol.
But theres a catch, lets say I have a file krypt which has some text 'fun'
If I try to redirect some data using > then that text would simpy overwrite the fun text and the fun part would be removed.
So in that case >>(append) comes into play because it would not overwrite the data but simply add to it.
Coming to the quesiton, it simply instructed me to append /challenge/run to /home/hacker/the-flag and it would give me both half of the flags, but if overwritten(using > symbol) then only the second half would be obtained.
Me being curious as ever firstly I obtained the flag by appending it, but then I also wanted to see the overwriting in action so I also performed that and it only gave me the second half of the flag. Both can be seen below:
~~~
bash
piping



 /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{gTJhxp5gt7mjq7ow-UomD5zq5Ce.ddDM5QDL5AjN0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
~~~




The second half command:

~~~
bash
hacker@piping~appending-output:~$ /challenge/run > /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
xp5gt7mjq7ow-UomD5zq5Ce.ddDM5QDL5AjN0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
~~~
As observed I only got the second half as I overwrote and didnt append.


## Redirecting Errors
As I learnt above, that there are 3 standard streams, now comes in stderr and redirecting error.
I also learnt that the > operator actually refers to 1> by default which means redirecting some input to a file.
Whilst 2> refers to redirecting some error into a file.
As FD 2 is standard error while FD 1 is Standard Output.
In this question I had to redirect the output of /challenge/run to myflag and then redirect its error to instruction file and then I had to read the myflag file to obtain the flag.
~~~
bash
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{UB8c8o0zad2ru1kwYl8TzgK88yR.ddjN1QDL5AjN0czW}
~~~

## Redirecting Input
In this submodule I learnt about the < operator which is basically the reverse process of the '>' operator.
The > operator is used to redirect output whilst < operator is used to redirect input
Lets say there is a file krypt and I want to write data in it so I can perform this task by the < operator by passing the command krypt < thisisfuntome
This redirected the input and is now stored in krypt so now if I read the cat file it would return thisisfuntome.
In the question I was required to redirect the input PWN to /challenge/run but before that I had to redirect COLLEGE to PWN.
~~~
bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ cat PWN
COLLEGE
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{cnsyJR8Gyh3Wfdg_vdB0PvJ8yQb.dBzN1QDL5AjN0czW}
~~~

## Grepping Stored Result
this module brought back memories with the grep command and how it used to search through some file using some given text like pwn.college to find the flag.
So firstly in the question /challenge/run was to be redirected into data.txt and then data.txt was to be grepped to find the flag.
~~~
bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{Q13nb-mRQHHin8B6ZMaqkIW0ygY.dhTM4QDL5AjN0czW}
~~~
As you can see I used pwn.college with the grep command to locate the flag.

## Grepping Live Output
Learnt about piping and how it can be used to remove the 'middleman'. Basically what that means is one can use the pipe operator to chain multiple commands together, some argument or text can be straight written into(redirected into) some file.
In the question I was required to to pipe the input of /challenge/run and then find the flag by grepping.
~~~
bash
hacker@piping~grepping-live-output:~$ grep pwn.college /challenge/run
#!/opt/pwn.college/bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{Y_RB9GcMlcy97AJ4xfvBAk0oKE3.dlTM4QDL5AjN0czW}
~~~


## Grepping Errors
In this program I learnt how to grep through errors directly using the pipe operator |
Earlier I used the 2> operator and redirected the error into a file and then searched through it but in this question we do it directly by using piping.
at first I tried to /challenge/run 2>&1 which simply redirected the error but didnt grep through it as the piping operator hadnt been used.
Then I tried grepping in the same argument as the piping operator and it worked.
~~~
bash
/challenge/run 2>&1
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...

[FAIL] You did not satisfy all the execution requirements.
[FAIL] Specifically, you must fix the following issue:
[FAIL]   stderr of this process does not appear to be a pipe!
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | /challenge/data.txt
ssh-entrypoint: /challenge/data.txt: No such file or directory
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt


 hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{kL5fbxuU-g2pRJvK_9-9e6seWaK.dVDM5QDL5AjN0czW}
~~~

## Duplicating piped data with the tee
This module taught me about a very important feature in linux, well it really cant be called a feature more like a command which is extremely helpful.
The command which im talking about is the tee command, which is used as an intercept between the data redirection when piping is being done.
the tee command can display any errors which are encountered when data redirection is being done between 2 files.
So it is highly useful as if some error is encountered in the process of piping the terminal wont display what went wrong without the tee command, with the help of tee command the error would be displayed and then can be debugged easily.
In the question I was instructed to use tee and firstly figure out what could be wrong with the redirection of data from /challenge/pwn to /challenge/college.
Firstly i tried piping without the use of tee command which obviously didnt work, then i tried the tee command which for some reason kept giving me an error.
~~~
bash
hacker@piping~duplicating-piped-data-with-tee:/$ /challenge/pwn | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:/$ /challenge/pwn | tee /challenge/college
Processing...
You are trying to use 'tee' *instead* of /challenge/college. Use it *between*
/challenge/pwn and /challenge/college!
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee'
for debugging).
/challenge/pwn | tee pwn | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
~~~
Then after some tries I realized that i had to read the pwn file to figure out what could be wrong with it, which returned me this:
~~~
bash
hacker@piping~duplicating-piped-data-with-tee:/$ cat pwn
Usage: /challenge/pwn --secret [SECRET_ARG]
SECRET_ARG should be "gNb6Lfo6"
~~~
after obtaining the above result I ran the following commands and got the flag:
~~~
bash
hacker@piping~duplicating-piped-data-with-tee:/$ /challenge/pwn --secret gNb6Lfo6
Processing...
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee'
for debugging).
hacker@piping~duplicating-piped-data-with-tee:/$ /challenge/pwn --secret gNb6Lfo6 | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{gNb6Lfo6gF_xmc0SxJzAvi4riYP.dFjM5QDL5AjN0czW}
~~~


## Writing to multiple programs
In this module firstly learnt how to duplicate data to different files with the tee command.
using the echo command and pairing that up with the tee command, the same data can be redirected to two different files.
For example if I pass echo krypt | tee crypto > nite
what this does is firstly pipes the text krypt into the file crypto and then redirects it into the file nite so if I were to read from the files, crypto and nite using the cat command they would both give me the same output which is krypt.
Then I learnt about process substitution, which means that using the >(x) operator data can be transmitted to different files like done above with the tee command.
Now the x can be anything ranging from a file to even an absolute path as linux can treat even the file path as a program if used with the >() operator and hence redirect data to it in the same way as done with a file.
also learn about the >(rev) command which can redirect data and reverse its order.
for example if i were to pass echo nite | tee >(rev), this would firstly give me the stdout using the tee command but then reverse it due to the rev command being present.
output: 
nite
etin
Now keeping these in mind, I went onto the question in which I was required to redirect one file's output as input to two files.
Firstly I tried doing it without the >() for some reason which didnt do it correctly of course as the data wasnt being duplicated but I realized that and corrected it.
~~~
bash
/challenge/hack | tee >(/challenge/the)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
2113915077577315077
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) > /challenge/planet
ssh-entrypoint: /challenge/planet: Permission denied
Are you sure you're properly redirecting input into '/challenge/the'?
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
19757267602381827600
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{QSYVKfu7WstqFM8bMQdkuc4pcaQ.dBDO0UDL5AjN0czW}
~~~
actually when the terminal gave me the error alongside the statement are you redirecting it properly, that was basically the answer for me and i realized where I was going wrong. Hence I corrected the error by using the >() as it was supposed to be duplicated and got the flag.

## Split-Piping stderr and stdout
Now the question done previously came of huge help during this question because the >() was supposed to be used here as well, because I am simultaneously redirecting stderr from one file and stdoutt'ing it into the other file.
The only difference here was that I was supposed to redirct the stderr from one file to the other hence 2>() operator was to be used.
here I was supposed to redirect stderr from the 'hack' file to 'the' file and then redirect the stdout to the 'planet' file.
keeping the concepts of the previous question in mind, this wasnt too bad.
~~~
bash
 /challenge/hack 2>(/challenge/the) >(/challenge/planet)
It looks like you passed something like '>(something)' as an *argument* to
/challenge/hack rather than redirecting /challenge/hack's out/error to
'>(something)'. Remember, 'cmd1 >(cmd2)' does *NOT* redirect output of cmd1;
rather, it'll run cmd2, hook a file up to its standard input, and pass that
file as an argument to cmd1. If you want to redirect cmd1's output into that
file, you will need to do: 'cmd1 > >(cmd2)', which is equivalent to 'cmd1 |
cmd2'.
You must redirect my standard output into '/challenge/planet'!
You must redirect my standard error into '/challenge/the'!
Are you sure you're properly redirecting /challenge/hack's standard output into
'/challenge/planet'?
Are you sure you're properly redirecting /challenge/hack's standard error into
'/challenge/the'?
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) > >(/challenge/planet)
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{sokaSjZpRH-yNqs6ZHn486lG-eO.dFDNwYDL5AjN0czW}
~~~
here when I passed the uppermost command it displayed me an error which again was kind of a clue on how to properly redirect the error and input as I was first required to redirect the stderr using the 2> operator but at the same time redirecting it into the file using >() command so that it can be duplicated as it was supposed to be done with 2 files.
hence following that I passed in the same line > >() operator as again input was supposed to be redirected and duplicated at the same time.



 



