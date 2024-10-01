# Pondering Paths
## Position Elsewhere
Similar to the Position Thy Self module, here firstly had to enter /challenge/run which told me im currently in the wrong directory and gave me the correct directory which I have to relocate to using the cd command.
Specifically this:
Incorrect...
You are not currently in the /usr/aarch64-linux-gnu/include/gnu directory.
by using the cd command I changed my directory and then invoked the file which worked successfully.
## Code and the Output recieved:
cd /usr/aarch64-linux-gnu/include/gnu
hacker@paths~position-elsewhere:/usr/aarch64-linux-gnu/include/gnu$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{8hJwHjRDdtTmT2iIBkMrq07YgiN.ddDN1QDL5AjN0czW}
hacker@paths~position-elsewhere:/usr/aarch64-linux-gnu/include/gnu$
this gave me the flag as I changed the directory then invoked the file.
