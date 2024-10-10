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
