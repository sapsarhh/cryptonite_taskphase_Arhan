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
