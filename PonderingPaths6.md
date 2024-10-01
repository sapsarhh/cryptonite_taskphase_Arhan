# Pondering Paths
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
