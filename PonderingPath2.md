# Pondering Path 
## The PATH variable
Learnt about the PATH variable which acts a sort of a gateway for different commands and actually tells those commands where to locate different files.
Like the ls command knows where to locate the files it needs to display because of the PATH variable being set to some value by default.
for example if I run the ls command it would display me the files in the cwd but if I set PATH="" and then run the ls command, it would give me an error.
Coming to the question, if the run file is invoked from its absolute path then it would delete the flag file and I cant obtain the flag file.
but if I somehow remove the rm command(the irony is so ironic) by setting the PATH variable to "" then the rm command wont work and the run file cant remove the flag file and the flag would be obtained.
So just to check it out I tried both the cases where the rm command is remove to see the output and also when the rm command wasnt removed.
~~~
bash
hacker@path~the-path-variable:~$ rm /flag
rm: remove write-protected regular file '/flag'?
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
Uh oh, looks like I successfully removed the flag! That means you did not
properly set PATH to keep me from finding 'rm'. Since the flag is gone, you
will need to re-launch the challenge from the module page! Better luck next
time.
~~~
Above is the case when the flag file gets removed as the PATH variable was set to default.

~~~
bash
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ rm /flag
ssh-entrypoint: rm: No such file or directory
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{Ql7P-53az63OvEP-GCNGIu9JTP9.dZzNwUDL5AjN0czW}
~~~
in the above output it can be seen, that the rm command doesnt work.

## Setting PATH
this one is described as doing something useful with the PATH variable and actually setting the path variable to some directory so that when that directory is invoked some specific file can be run.
in the question I have to set the path variable to the directory given so that on invoking /challenge/run file the win command is exeuted so that the flag can be displayed.
~~~
bash
hacker@path~setting-path:~$ PATH="/challenge/more_commands/"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{YDGh5s50kBDf4-Xq1SHJ3UXLNio.dVzNyUDL5AjN0czW}
~~~

## 

