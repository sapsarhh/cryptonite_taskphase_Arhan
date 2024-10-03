# Digesting Documentation
## Learning from Documentation 
This module taught me the importance of documentation. Which is basically a way of figuring out how to run different programs through different ways.
What I mean by different ways can be understood by an example which the module has provided, which also helped me learn or better yet understand it.
lets say i run the ls command, it shows me all of the files but not the hidden ones.
Then I run the ls -a command where -a is an argument which is telling or instructing linux to display the hidden files as well.
Hence an addition command(argument) can also be given in order to perform some specific task in addition to the task already being done.
With this information, i try the module in which I basically have to invoke the program /challenge/challenge but I have to do it with an addition argument which is --giveflag
I first run the command below which gave me an error and I quickly realized that I dont have to pass the argument in that way.

~~~
bash
/challenge/challenge ~/giveflag
Incorrect usage! You passed the wrong argument (read the challenge description
for details).
~~~
Then I do it correctly by using the below commands.
~~~
bash
/challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{I9T0_MEoXLGureKJ6lcbnVlD1I1.dRjM5QDL5AjN0czW}
~~~

## Learning Complex Usage
In this module, I learnt about the --printfile argument which can be used to read a specific file's contents.
It is different from the cat command as printfile is an argument.
Then as the module instructed me the I cd'ed into the / directory.
But I did commit some mistakes before I got the flag as firstly I read the description.md file which gave me the details of the module itself.
then /challenge/challenge --printfile /challenge/flag but that didnt work out.
But after that I realized why this was wrong as I was already looking in the /challenge directory so I didnt have to refer to it again whilst using the printfile argument.
Hence I used the following command and got the flag /challenge/challenge --printfile /flag
~~~
bash
 cd /
/challenge/challenge --printfile /challenge/flag
Correct argument! Here is the /challenge/flag file:
cat: /challenge/flag: No such file or directory
~~~
This above was the error which i encountered.
~~~
bash
challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{MLDGmsLl1wvc1iO-LLsI8KjULHd.dVjM5QDL5AjN0czW}
~~~


