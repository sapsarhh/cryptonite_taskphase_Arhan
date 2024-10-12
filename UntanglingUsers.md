# Untangling Users
Learnt that there are many users on the linux terminal, not only the root and hacker users.
the list of all these users can be displayed by the invoking the /etc/passwd file.
in this module I learn how to change the user by the su and the sudo command and not by changing the permissions or the group of the user by the chmod or chgrp command.
su stands for switching user which is not really used anymore.

## Becoming Root with su
in the question I learnt how to use the su command and how to change the user with it.
I learnt that when the su command is used, the user has to enter a password to successfully change the root user to access different files.
In the question I was given the password which had to be entered after the su command was invoked.
~~~
bash
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{84COlQ8c6HVyMkaEuSV0CO5BCK_.dVTN0UDL5AjN0czW}
~~~

## Other Users with su
In the following module I learnt that the su command not only can change the user to the root user, it can also change it to different users.
by default it changes it to the root user but if some valid user name is given in front of the su command, it would change the user to that provided the password is correct.
in the question I was required to change the user to zardus and enter the password, then invoke the run file.
~~~
bash
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ cat /flag
cat: /flag: Permission denied
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{UhltkX6lS8teltKA0gUrLVe1pFv.dZTN0UDL5AjN0czW}
~~~

## Cracking Passwords
this question definitely piqued my interest.
firstly in the module I learnt that earlier /etc/passwd used to contain all the passwords of all users, but that was a globally readable file hence that was changed and now the /etc/shadow file contains the passwords which cant be opened normally obviously.
but when one becomes root even then reading passwords isnt easy from this file as they all have been encrypted or hashed.
this is where john the ripper comes into play, this is not exactly built-in the linux terminal, has to be installed but for our easy convienence it is inside the terminal(thanks pwn.college).
so by using the john command that password is decrypted and then can be entered once the su command is run and it changes the user.
in this question I didnt know the password to su to zardus so firstly I had to read the shadow-leak file to obtain the encrypted password, then I had to run the john command with the shadow-leak file to obtain the password and use it with the su command to change the user.
~~~
bash
hacker@users~cracking-passwords:~$ /challenge/shadow-leak
ssh-entrypoint: /challenge/shadow-leak: Permission denied
hacker@users~cracking-passwords:~$ cat /challenge/shadow-leak
root:*:19873:0:99999:7:::
daemon:*:19873:0:99999:7:::
bin:*:19873:0:99999:7:::
sys:*:19873:0:99999:7:::
sync:*:19873:0:99999:7:::
games:*:19873:0:99999:7:::
man:*:19873:0:99999:7:::
lp:*:19873:0:99999:7:::
mail:*:19873:0:99999:7:::
news:*:19873:0:99999:7:::
uucp:*:19873:0:99999:7:::
proxy:*:19873:0:99999:7:::
www-data:*:19873:0:99999:7:::
backup:*:19873:0:99999:7:::
list:*:19873:0:99999:7:::
irc:*:19873:0:99999:7:::
gnats:*:19873:0:99999:7:::
nobody:*:19873:0:99999:7:::
_apt:*:19873:0:99999:7:::
hacker::20000:0:99999:7:::
zardus:$6$oES9EtBhFEvt.HV7$s4SyMRJv3yS7zWmuDuhXfyVxMEBlGMdEf7NpBMln.OEf5B9LfwzhvGjWGVrywtTHsQWPMnBnVMmrt8qdv8YEv/:20008:0:99999:7:::
hacker@users~cracking-passwords:~$ john
Created directory: /home/hacker/.john
John the Ripper password cracker, version 1.8.0
Copyright (c) 1996-2013 by Solar Designer
Homepage: http://www.openwall.com/john/

Usage: john [OPTIONS] [PASSWORD-FILES]
--single                   "single crack" mode
--wordlist=FILE --stdin    wordlist mode, read words from FILE or stdin
--rules                    enable word mangling rules for wordlist mode
--incremental[=MODE]       "incremental" mode [using section MODE]
--external=MODE            external mode or word filter
--stdout[=LENGTH]          just output candidate passwords [cut at LENGTH]
--restore[=NAME]           restore an interrupted session [called NAME]
--session=NAME             give a new session the NAME
--status[=NAME]            print status of a session [called NAME]
--make-charset=FILE        make a charset, FILE will be overwritten
--show                     show cracked passwords
--test[=TIME]              run tests and benchmarks for TIME seconds each
--users=[-]LOGIN|UID[,..]  [do not] load this (these) user(s) only
--groups=[-]GID[,..]       load users [not] of this (these) group(s) only
--shells=[-]SHELL[,..]     load users with[out] this (these) shell(s) only
--salts=[-]N               load salts with[out] at least N passwords only
--save-memory=LEVEL        enable memory saving, at LEVEL 1..3
--node=MIN[-MAX]/TOTAL     this node's number range out of TOTAL count
--fork=N                   fork N processes
--format=NAME              force hash type NAME: descrypt/bsdicrypt/md5crypt/
                           bcrypt/LM/AFS/tripcode/dummy/crypt
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04914g/s 286.1p/s 286.1c/s 286.1C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su
WARNING: you are invoking 'su' without specifying a user. This will default to
the 'root' user, which is not achievable in this challenge.
Password:
su: Authentication failure
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{swlTQ2JteiMSXqs4Toiu4Cd7F8-.ddTN0UDL5AjN0czW}
~~~

## Using sudo
In this module I learnt about the sudo(superuser do) command which is basically the newer su command which is so powerful that it doesnt even require a password like su did(su's security is nothing in front of sudo as the password can be leaked) rather sudo works on policies and the authentication of the user.
by default sudo also changes the user to root just like su.
but sudo is better in terms of obtaining the flag as lets say the user is hacker and the hacker user tries to grep through the flag and read it, of course it would give an error but if you use the command sudo with the grep command then it would work as it is simultaneously changing the user to root and also grepping through the flag.
In the question I was supposed to sudo and then grep through the flag file which I handled pretty well.
~~~
bash
sudo
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user] [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p prompt] [-T timeout] [-u user]
            [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p prompt] [-T timeout] [-u user] file ...
hacker@users~using-sudo:~$ sudo grep pwn.college /flag
pwn.college{4kDH9K-9wTOK38kENqkk4uRR56m.dhTN0UDL5AjN0czW}
~~~


