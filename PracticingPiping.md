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




 



