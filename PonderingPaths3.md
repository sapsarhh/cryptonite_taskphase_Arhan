# Pondering Paths
## Position Thy Self
Got to know more about the cd command which stands for change directory, cd is used to go into some specific directory and then invoke some program inside that directory.
Lets say I try to invoke some specifc when im not in the right directory it would give me an error but if that specific file exists in that directory then that file can only be invoked if im inside that specifc directory which is done by the cd command.
Now in the module, first we had to input the command /challenge/run which is incorrect and it gave me the specifc error: 
challenge/run
Incorrect...
You are not currently in the /usr/bin directory
and in the module it says that the terminal would tell me the right directory hence I need to change my directory using the cd command to /usr/bin to invoke the program correctly.
## Code and the Output recieved:
/usr/bin$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{wOvSp-tm6CP4ghSJkq2Q90vUOmG.dZDN1QDL5AjN0czW}
As I changed my directory to /usr/bin, now the file was invoked correctly and I recieved the flag.
