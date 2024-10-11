# Processes and Jobs
## Listing Processes
Learnt about the ps command, which by default is used to list out all the processes running in the terminal.
it also lists the terminal on which currently the commands are being run on and also the total amount of cpu time the process has used up so far.
to make the ps command useful, specific arguments are passed with it to make it more useful.
these specific commands can be -e which is used to list every process or a to list out all files of all users, u for user readable output and x to list out processes that arent running in a terminal.
these can also be combined like aux to list all of the above characteristic files.
in the question the /challenge/run file was renamed specifically the run file was renamed to something else and using the ps command with some arguments, I was required to find that file and run that to obtain the flag.
In the question I firstly ran the ls command with the -e argument but that wasnt of any help, then with the a command which also didnt help and then finally with the aux argument which listed all files and displayed the /challenge file which was of course the file required to obtain the flag.
~~~
bash
hacker@processes~listing-processes:~$ ps -e
    PID TTY          TIME CMD
      1 ?        00:00:00 docker-init
      7 ?        00:00:00 /run/dojo/bin/s
     68 ?        00:00:00 bash
     72 ?        00:00:00 sleep
     73 pts/0    00:00:00 ssh-entrypoint
     90 pts/0    00:00:00 ps
hacker@processes~listing-processes:~$ ps a
    PID TTY      STAT   TIME COMMAND
     73 pts/0    Ss     0:00 /run/dojo/bin/ssh-entrypoint
     91 pts/0    R+     0:00 ps a
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.5  0.0   1056   640 ?        Ss   18:25   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bi
root           7  0.1  0.0   5052  2240 ?        S    18:25   0:00 /run/dojo/bin/sleep 6h
root          68  0.0  0.0   4132  2560 ?        S    18:25   0:00 /challenge/2976-run-15542
root          72  0.0  0.0   2744  1600 ?        S    18:25   0:00 sleep 6h
hacker        73  0.4  0.0   5376  3840 pts/0    Ss   18:25   0:00 /run/dojo/bin/ssh-entrypoint
hacker        92  0.0  0.0   7868  3520 pts/0    R+   18:25   0:00 ps aux
hacker@processes~listing-processes:~$ /challenge/2976-run-15542
Yahaha, you found me! Here is your flag:
pwn.college{YHKCpc0s59Mmqf1qHsNCa8HPf_b.dhzM4QDL5AjN0czW}
Now I will sleep for a while (so that you could find me with 'ps').
~~~


## Killing Processes
in this module I learnt about the kill command, which is of course used to terminate programs running in the terminal. also learnt that passing only the file name as an argument using the kill command doesnt work instead the job id has to be provided to terminate that file.
in the question I was instructed to terminate the dont_run file and then invoke the run file.
firstly I tried killing the file directly using its file path which didnt work as the job id is required, that is when I realized that the ps command would have to be used so as to obtain the id of the program and then using that to terminate it.
~~~
bash
hacker@processes~killing-processes:~$ kill /challenge/dont_run
ssh-entrypoint: kill: /challenge/dont_run: arguments must be process or job IDs
ps -e
    PID TTY          TIME CMD
      1 ?        00:00:00 docker-init
      7 ?        00:00:00 /run/dojo/bin/s
     71 ?        00:00:00 su
     73 ?        00:00:00 bash
     74 ?        00:00:00 sleep
     75 pts/0    00:00:00 ssh-entrypoint
     98 pts/0    00:00:00 ps
hacker@processes~killing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   18:39   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bi
root           7  0.0  0.0   5052  2560 ?        S    18:39   0:00 /run/dojo/bin/sleep 6h
root          71  0.0  0.0   4732  2560 ?        S    18:39   0:00 su -c /challenge/.launcher hacker
hacker        73  0.0  0.0   4976  3200 ?        Ss   18:39   0:00 /challenge/dont_run
hacker        74  0.0  0.0   5052  2560 ?        S    18:39   0:00 sleep 6h
hacker        75  0.1  0.0   5376  3520 pts/0    Ss   18:40   0:00 /run/dojo/bin/ssh-entrypoint
hacker        99  0.0  0.0   7868  3520 pts/0    R+   18:40   0:00 ps aux
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{0x3w33ZqUXxQxLbHLWq4MJyTvmi.dJDN4QDL5AjN0czW}
~~~

## Interrupting Processes
learnt how to interrupt a file while its awaiting its input by the user, this exits the file.
the shortcut to do this is to use the keys ctrl and c together basically holding down the ctrl button and then pressing the c key.
in the question I was required to invoke the run file and whilst its awaiting its input, use the ctrl+c combination to interrupt and exit it.
~~~
bash
/challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{g3gC7-oXPJVFlAWKe0XFgksMjiu.dNDN4QDL5AjN0czW}
~~~

## Suspending Processes
Just like the last question, in this instead of interrupting processes we can suspend them using the combination ctrl+z when the file is awaiting its input.
in the question I had to suspend the run file and then whilst the file was suspened, I had to run it again to obtain the flag.
~~~
bash
/challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 19:00 pts/0    00:00:00 bash /challenge/run
root          84      82  0 19:00 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 19:00 pts/0    00:00:00 bash /challenge/run
root          89      65  0 19:00 pts/0    00:00:00 bash /challenge/run
root          91      89  0 19:00 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{UGEHykszdG7eLlnSKBrOAoktFt7.dVDN4QDL5AjN0czW}
~~~

## Resuming Processes
when a file is suspended it can be resumed otherwise it wont be any different than terminating the file and it would be better to just terminate it.
using the fg command, a suspended file can be resumed.
in the question I was required to suspend the run file and then resume it using the fg command.
~~~
bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{4x6qqSHWz2iStQa3XGzZQZvTJch.dZDN4QDL5AjN0czW}
Don't forget to press Enter to quit me!

Goodbye!
hacker@processes~resuming-processes:~$
~~~

## Backgrounding Processes
In this module I learnt how to run a program in the background of the terminal.
the file can be put in the background and other files can be run whilst that file is in the background.
this can be done by using the bg command.
in this question, I was required to firstly suspend the run by using the key combination ctrl+Z then I was supposed to background it using the bg command then whilst the run file was already running in the background I had to invoke it again to obtain a flag.


~~~
bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root          92 S    sleep 6h
root          93 S+   bash /challenge/run
root          95 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{MkrbXx2O8V7uw8K_pqI3nkk3Ag_.ddDN4QDL5AjN0czW}
~~~

## Foregrounding Processes
In this module I learnt how to foreground a process, foregrounding basically means when a file is already suspended, it is run in the background and then when its in the background, the fg command is used to resume the process whilst it was in the background.
so in this question I was basically supposed to foreground the run file so firstly suspend it using the ctrl+Z command, then run it in the background using the bg command, then resume that file using the fg command which basically foregrounds it.
~~~
bash
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &



hacker@processes~foregrounding-processes:~$ Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg /challenge/run
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{4f5sxYIir0HkRUfzrKRSgHWr_fV.dhDN4QDL5AjN0czW}
~~~

## Starting Background Processes
In this module I learnt how to run a file in the background using the & command. Firstly in the question I thought that I had to pass the & operator with the run file with its job id to keep it running in the background but that wasnt required, I could directly run it in the background using the & command.
as you can see the code below I used the ps command with the aux argument at first to obtain the job id of the run file but that wasnt required and the & operator could be used directly.
~~~
bash
ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.0   1056   640 ?        Ss   10:14   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bi
root           7  0.0  0.0   5052  2240 ?        S    10:14   0:00 /run/dojo/bin/sleep 6h
hacker        65  0.1  0.0   5360  3840 pts/0    Ss+  10:14   0:00 /run/dojo/bin/ssh-entrypoint
hacker        82  0.2  0.0   5360  3840 pts/1    Ss   10:14   0:00 /run/dojo/bin/ssh-entrypoint
hacker        99  0.0  0.0   7868  3520 pts/1    R+   10:14   0:00 ps aux
hacker@processes~starting-backgrounded-processes:~$ /challenge/run
You've started me in the foreground! You must start me in the background (by
appending '&' to the command) to get the flag!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 103
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{4zNr5ltaEqMMB5Nmq70z1CsSaSV.dlDN4QDL5AjN0czW}

[1]+  Done                    /challenge/run
~~~


## Process Exit Codes
Learnt how to obtain the error code of some specific command passed in the linux terminal. 
The error code can be obtained by the $? operator which can either return 0 or some non zero value(most commonly 1).
where 0 is returned if some process is successfully run but if it doesnt run then the error code is 1 or some non zero value as said above.
this is actually in contrast to coding languages, because if a condition is true in a langauge then it returns the value 1 and if false then 0.
anyways coming back to the question I was required to print the error code of the get-code file and use that error code with submit-code.
on a sidenote i found the $? very fascinatinng because it is so dynamic in the sense that the error code changes after every command inputted in the terminal, this can be seen below in the code as I made a mistake due to this.
~~~
bash
 /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ $?
ssh-entrypoint: 182: command not found
hacker@processes~process-exit-codes:~$ echo $?
127
 /challenge/submit-code 127
Incorrect... Make sure to use $? immediately after running /challenge/get-code.
Your shell will overwrite the $? variable with the exit value of any other
command you run!
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
41
hacker@processes~process-exit-codes:~$ /challenge/submit-code 41
CORRECT! Here is your flag:
pwn.college{8JoARowdH9ShOHR23Y_g6FAGrMA.dljN4UDL5AjN0czW}
~~~
