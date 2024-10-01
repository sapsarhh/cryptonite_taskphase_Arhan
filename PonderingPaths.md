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

## Position Thy Self
Got to know more about the cd command which stands for change directory, cd is used to go into some specific directory and then invoke some program inside that directory.
Lets say I try to invoke some specific file when im not in the right directory it would give me an error but if that specific file exists in that directory then that file can only be invoked if im inside that specifc directory which is done by the cd command.
Now in the module, first we had to input the command /challenge/run which is incorrect and it gave me the error which can be seen below in the code. 
As I changed my directory to /usr/bin, now the file was invoked correctly and I recieved the flag.
In the module it says that the terminal would tell me the right directory hence I need to change my directory using the cd command to /usr/bin to invoke the program correctly.
~~~
bash
challenge/run
Incorrect...
You are not currently in the /usr/bin directory
and in the module it says that the terminal would tell me the right directory hence I need to change my directory using the cd command to /usr/bin to invoke the program correctly.
/usr/bin$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{wOvSp-tm6CP4ghSJkq2Q90vUOmG.dZDN1QDL5AjN0czW}
~~~


## Position Elsewhere
Similar to the Position Thy Self module, here firstly had to enter /challenge/run which told me im currently in the wrong directory and gave me the correct directory which I have to relocate to using the cd command.
The error is displayed in the code below. By using the cd command I changed my directory and then invoked the file which worked successfully.
This gave me the flag as I changed the directory then invoked the file.
~~~
bash
Incorrect...
You are not currently in the /usr/aarch64-linux-gnu/include/gnu directory.
cd /usr/aarch64-linux-gnu/include/gnu
hacker@paths~position-elsewhere:/usr/aarch64-linux-gnu/include/gnu$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{8hJwHjRDdtTmT2iIBkMrq07YgiN.ddDN1QDL5AjN0czW}
hacker@paths~position-elsewhere:/usr/aarch64-linux-gnu/include/gnu$
~~~

## Position Yet Elsewhere
Similar to the last 2 modules, in this one I had to change the directory again as I was not in the correct directory, hence when I try to invoke the /challenge/run file it gives me an error but tells me the correct directory which I need to change to.
Recieved this specific output
So, by using the cd command I changed my directory to the directory given by the console/terminal and then invoked the program.
As you can see firstly I changed my directory to /var/lib/apt/lists and then invoked the file which gave me the flag.
~~~bash
/challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.


cd /var/lib/apt/lists
hacker@paths~position-yet-elsewhere:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{wgp_HkK7KTFNcSkgVysaauctjlU.dhDN1QDL5AjN0czW}
hacker@paths~position-yet-elsewhere:/var/lib/apt/lists$

~~~

## Implicit Relative Paths, from /
In this module, I learnt about the difference of relative and absolute path. Relative path is basically different in the sense that it can be called when youre currently in a cwd(current working directory).
lets say im currently inside the / directory and I need to change my path I can do this by simply typing challenge/run which is a relative path and not an absolute one, contrary to that the absolute path here would be
/challenge/run that directly changes my path to / and then invokes the file after it.
Reffered to the following video for more information on both of the path types: https://www.youtube.com/watch?v=sB77xnFhsJs&ab_channel=TheLinuxJuggernaut
Then I changed my directory to / by using cd / as earlier it showed an error due to incorrect directory.
This changed the directory to / and then by using the relative path invoked the file successfully and gave me the flag.
~~~
bash
/challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
Then I changed my directory to / by using cd /
## Commands and The Result:
cd /
challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{c-bzIpZbYMPuNzpT-oMxKwM3gO_.dlDN1QDL5AjN0czW}
~~~

## Explicit Relative Paths, from /
As it says in the module body, in the previous module the relative path was naked and I was just calling it by not giving a / assuming my directory was already /, and then i could have called it by just passing /challenge/run 
But now there are other ways of calling a relative path by using ., .. or even ... which basically refer to the same directory.
for example challenge/run refers to the same ./challenge/run
in this module we have to refer to the relative path by using the . to refer to the current directory.
hence firstly I change my directory to / by using cd / 
then by using a little trial and error and type /challenge/run but the terminal tells me this is incorrect for the specific module as "This challenge must be called with a relative path that explicitly starts with a `.`!"
then I know that I have to start with a . so I try the command ./challenge/run to invoke the file by using that explicit relative path and it works.
~~~
bash
 ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{wwhjNkHRUw59WT7AB5cw_gbsNpd.dBTN1QDL5AjN0czW}
~~~

## Implicit Relative Path
In this module, I explore more about implicit relative paths. I also learn a very important concept which is a kind of a safety measure which linux uses. The module body tells and educates me by giving me an example that if I change my directory to lets say /challenge by using the cd command and then invoke some file run inside of /challenge .
then as a safety measure it would give me an error that run command is an invalid command, so that one mistakenly doesnt execute programs in the current directory that might have the same name as the core system utilities.
then by using some trial and error I ran some commands which didnt work, but after reading the question a several times, it was clear that i didnt have to use the cd command but only the run command and that too explicitily.
so i tried the ./run command which worked and i obtained the flag.
~~~
bash
 ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{0qD-ul0DZU0G03nqrM4fId5YYL-.dFTN1QDL5AjN0czW}
hacker@paths~implicit-relative-path:/challenge$
~~~


## home sweet home
used the following video -----> https://www.youtube.com/watch?v=Gexu9M7p5aU&ab_channel=ProgrammingKnowledge as a reference because I did not know how to pass arguments. watching that video I then learnt how to do it and what is the specific command for it.
~~~
bash
/challenge/run ~/e
Writing the file to /home/hacker/e!
... and reading it back to you:
pwn.college{YbsFjzwQfHRfh4uEvnKHKcpkThX.dNzM4QDL5AjN0czW}

~~~

