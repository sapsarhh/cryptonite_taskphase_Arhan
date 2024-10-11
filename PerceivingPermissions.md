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

