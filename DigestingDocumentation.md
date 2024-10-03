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

## Reading Manuals
In this module, I learnt about the manual command which as actually exectued in short as man command and it gives the details about some specific command written in front of it.
For example, lets say I want to more about the cat command and want its manual, then I could just type man cat into the terminal and it would give me the following result:

~~~
bash

NAME
       cat - concatenate files and print on the standard output

SYNOPSIS
       cat [OPTION]... [FILE]...

DESCRIPTION
       Concatenate FILE(s) to standard output.

       With no FILE, or when FILE is -, read standard input.

       -A, --show-all
              equivalent to -vET

       -b, --number-nonblank
              number nonempty output lines, overrides -n

       -e     equivalent to -vE

       -E, --show-ends
              display $ at end of each line

       -n, --number
              number all output lines

       -s, --squeeze-blank
              suppress repeated empty output lines

       -t     equivalent to -vT

       -T, --show-tabs
              display TAB characters as ^I

       -u     (ignored)

       -v, --show-nonprinting
              use ^ and M- notation, except for LFD and TAB
~~~

I also learnt that in corellation to the man command, the actual path which man refers to is /usr/share/man, but one cant use this path to get the same result as given by the man command.
Lets say I write 
~~~
bash
/usr/share/man --printfile /cat
ssh-entrypoint: /usr/share/man: Is a directory
~~~
so it basically shows me this instead of the manpage.
Then as the question said that I have to get clues from the manual of challenge, hence I used the command man challenge
which showed me the following:
~~~
bash
CHALLENGE(1)                                    Challenge Commands                                   CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --uemmfa NUM
              print the flag if NUM is 345

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)
~~~
from this I could see that there was a file --uemmfa NUM which could read the file.
hence I cd into the directory /
/challenge/challenge --uemmfa NUM
Incorrect usage! Please read the challenge man page!
firstly I used the above commands and arguments but that didnt work.
But after the following hit and trial the commands worked and I got the flag:
~~~
bash
challenge --uemmfa NUM
ssh-entrypoint: /challenge: Is a directory
hacker@man~reading-manuals:/$ --uemmfa NUM
ssh-entrypoint: --uemmfa: command not found
hacker@man~reading-manuals:/$ /challenge --uemmfa 345
ssh-entrypoint: /challenge: Is a directory
hacker@man~reading-manuals:/$ /challenge/challenge --uemmfa 345
Correct usage! Your flag: pwn.college{MRIueURmPmfaEyzEFoC-HKn3pVk.dRTM4QDL5AjN0czW}
~~~
As I realized that the flag would only print if the num is 345 so I did that by referring the printfile to /challenge/challenge directory.


## Searching Manuals
As this I learnt that some symbols on the keyboard like / ? etc can be used to search within a manual.
With that information in mind I tried the question as it told me to search within the challenge manual.
After using the man challenge command, luckily the first thing I did was to use the / symbol and search for flag inside the file and the first result I found was --odz  This argument will give you the flag, so I basically invoked the file and that was it.
/challenge/challenge --odz
Initializing...
Correct usage! Your flag: pwn.college{4Rei-VwuZ3XAWEZxR7-JSzk8fsi.dVTM4QDL5AjN0czW}


