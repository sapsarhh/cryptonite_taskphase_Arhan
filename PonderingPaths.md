# Pondering Paths
## The Root
In this module, the learning that I took is that a file system starts with /, lets say I pass a command / inside the terminal, it would just give me the root directory name.
All the directories and files are located inside the directory.
then I passed the specific command: /pwn which basically referred to the program pwn and invoked it.
~~~
bash
(ssh-entrypoint: /: Is a directory).
/pwn
BOOM!!!
Here is your flag:
pwn.college{I3h-tdqD8RczpA2gW_PatJ-mqwM.dhzN5QDL5AjN0czW}
and then I successfully recieved the flag for that module.
~~~

## Program and Absolute Paths
As the name of the module suggests, I learnt about the absolute paths of a specific file inside a directory, like how a subfolder can be created inside a specific folder and that folder can be referred to as /folder/newfolder just to give an example.
As the challenge said I just had to invoke a file 'run' which was inside another file 'challenge' and the said file was invoked using the command------> /challenge/run which did nothing but invoked the run file whilst reffering to its absolute path which was inside challenge and the first / refers to the root directory.
Reffered to following video explaining the difference between a relative path and an absolute path: https://www.youtube.com/watch?v=ephId3mYu9o&ab_channel=Udacity
~~~
bash
/challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{4RrwN0a81oVhRgO5DxMzPu13EjD.dVDN1QDL5AjN0czW}
~~~

