# Pondering Paths
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
