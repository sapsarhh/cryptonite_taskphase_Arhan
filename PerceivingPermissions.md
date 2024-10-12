# Perceiving Permissions
## Intro
Firstly learnt about the -l argument which can be used with the ls command which has come previously and is used to display all the files in some directory.
the -l argument is used to view the file types and the various permissions a file can have and also the ownership of the file.
there are some characteristics which are used and through which the file type and permissions are known such as the first letter.

## Changing File Ownership
Learnt alot of things in this module like how the ultimate power of a terminal lies in the hands of root also how to change the user of a specific file so that the hacker user(in this case) can read it.
the above can be done by the chown command which basically means changing the user of some file.
the syntax of chown is chown [username] [filename]
so lets say i have a file crypt which can only be read by the user root, so i can change its access by passing chown hacker crypt and then cat it successfully.
in the question I was instructed to change the ownership of the flag file so that the user hacker(me) could read it.
~~~
bash
chown hacker /flag
hacker@permissions~changing-file-ownership:/$ cat flag
pwn.college{wrp5L219JC6I28_uYKK0TmJlFxm.dFTM2QDL5AjN0czW}
~~~

## Groups and Files
firstly learnt about groups, in linux users are by default part of a group, file permissions reside with a group like the users of the root group have access to all the files, but some other members of a group of course wont have all the permissions.
then learnt about the id command which is used to display all the different groups present inside the terminal.
lastly learnt about the chgrp command which is used to change the group of a user so that the user can access different or more files depending upon the new group which they are now a part of.
In the question I was required to change the group of the user hacker(me) so that I can access and read the flag file using the cat command.
~~~
bash
id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~groups-and-files:~$ chgrp groups /flag
chgrp: invalid group: ‘groups’
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{0YJ2TkFDSaJNRbGfuKAMw6F0DqO.dFzNyUDL5AjN0czW}
~~~


## Fun with Group Names
learnt that every user is already part of their own group like the user hacker is already a part of the hacker group.
in the question I was required to use the id command to find the different names of groups as the name of the hacker group had been changed.
so by using the id command I did a little hit and trial and obtained the flag
~~~
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp7279) groups=1000(grp7279)
hacker@permissions~fun-with-groups-names:~$ chgrp gid /flag
chgrp: invalid group: ‘gid’
hacker@permissions~fun-with-groups-names:~$ chgrp groups /flag
chgrp: invalid group: ‘groups’
hacker@permissions~fun-with-groups-names:~$ chgrp grp7279 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{Q77v8dl6TNu2oVJ0pG0nmFUkmn_.dJzNyUDL5AjN0czW}
~~~


## Changing Permissions
learnt about the highly important chmod command, which is used to change the permissions of the file.
different modes can be used with the chmod command, these modes can be anything like reading, writing to the file basically accessing the file.
modes include u+r(used to give the user the permissions to read the file), g+wx which adds write and execute access to the group of the user.
the question actually was pretty difficult as it required me to actually leave the ubuntu terminal and research the net for more information on the chmod command as nothing I was doing on the terminal worked.
~~~
bash
hacker@permissions~changing-permissions:~$ chmod u+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~changing-permissions:~$ ls -l /flag
-r-------- 1 root root 58 Oct 12 19:36 /flag
hacker@permissions~changing-permissions:~$ chmod u+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~changing-permissions:~$ chgrp hacker /flag
chgrp: changing group of '/flag': Operation not permitted
hacker@permissions~changing-permissions:~$ id f
id: ‘f’: no such user
hacker@permissions~changing-permissions:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~changing-permissions:~$ chmod r /flag
chmod: invalid mode: ‘r’
Try 'chmod --help' for more information.
hacker@permissions~changing-permissions:~$ /f
ssh-entrypoint: /f: No such file or directory
hacker@permissions~changing-permissions:~$ /flag
ssh-entrypoint: /flag: Permission denied
hacker@permissions~changing-permissions:~$ chmod g+wx /flag
hacker@permissions~changing-permissions:~$ /flag
ssh-entrypoint: /flag: Permission denied
hacker@permissions~changing-permissions:~$ cat /flag
cat: /flag: Permission denied
~~~
firstly I expected the u+r mode to work but that didnt work, then I tried the g+wx mode and tried to invoke the file but that also didnt work, when nothing worked I tried to get help from the --help argument but that was also useless.
Then finally I gave up all hope after some reapeated failed attempts and surfed the net for more info on the chmod command.
Some info which I got was basically that chmod mode can have octal numbers infront of them and one in particular can be used to give the user access to read the file which was the number 644 as 6 is for -rw while 4 is for -r where r is reading and rw is writing to the file.
source-----> https://www.pluralsight.com/blog/it-ops/linux-file-permissions
then I used the chmod command with the octal digits and it worked.
~~~
bash
hacker@permissions~changing-permissions:~$ chmod 644 /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{8yCwMj0bTZXmHJYzpUo_TYxLItL.dNzNyUDL5AjN0czW}
~~~


## Executable Files
learnt that of course not only the reading permissions but also the invoking and accessing permissions of a file can be changed by the chmod command.
in the question I was required to change the permissions of the /run file so that it could be invoked by the hacker user.
past experience taught me that chmod command wouldnt work normally, but I still tried the following
~~~
bash
hacker@permissions~executable-files:~$ chmod g+wx /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
ssh-entrypoint: /challenge/run: Permission denied
~~~
but now I knew that octal numbers worked with the chmod command so I checked the above website again and found that 700 would work as 0 is -- while 7 is rwx which gives all the permissions to the user such as reading writing and invoking.
So I did that to obtain the flag.
~~~
bash
hacker@permissions~executable-files:~$ chmod g+wx /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
ssh-entrypoint: /challenge/run: Permission denied
~~~

## Permission Tweaking Practice




