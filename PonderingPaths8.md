# Pondering Paths
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
