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

