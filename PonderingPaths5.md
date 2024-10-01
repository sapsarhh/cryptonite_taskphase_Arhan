# Pondering Paths 
## Position Yet Elsewhere
Similar to the last 2 modules, in this one I had to change the directory again as I was not in the correct directory, hence when I try to invoke the /challenge/run file it gives me an error but tells me the correct directory which I need to change to.
Recieved this specific output:
/challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.
So, by using the cd command I changed my directory to the directory given by the console/terminal and then invoked the program.
## Code and Output recieved:
cd /var/lib/apt/lists
hacker@paths~position-yet-elsewhere:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{wgp_HkK7KTFNcSkgVysaauctjlU.dhDN1QDL5AjN0czW}
hacker@paths~position-yet-elsewhere:/var/lib/apt/lists$
As you can see firstly I changed my directory to /var/lib/apt/lists and then invoked the file which gave me the flag.
