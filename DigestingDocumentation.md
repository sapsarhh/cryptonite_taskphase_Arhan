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
But after the following hit and trial the commands worked and I got the flag as I didnt realized that I had to enter the actual number until I tried it:
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
In this module I learnt that some symbols on the keyboard like / ? etc can be used to search within a manual.
With that information in mind I tried the question as it told me to search within the challenge manual.
After using the man challenge command, luckily the first thing I did was to use the / symbol and search for flag inside the file and the first result I found was --odz  This argument will give you the flag, so I basically invoked the file and that was it.
~~~
/challenge/challenge --odz
Initializing...
Correct usage! Your flag: pwn.college{4Rei-VwuZ3XAWEZxR7-JSzk8fsi.dVTM4QDL5AjN0czW}
~~~

## Searching for Manuals
In this module firstly I had to read and go through the man man page.
If i invoke or run the above command then it would display to me the manual page for the man command.
I ran the above command and searched through the manual page for something that would help me in running a command or an argument which would return me the flag.
When I was going through the manual one thing which caught my eye was this specific argument:
   ~~~

   Main modes of operation
       -f, --whatis
              Equivalent to whatis.  Display a short description from the manual page, if available.  See whatis(1) for details.

       -k, --apropos
              Equivalent to apropos.  Search the short manual page descriptions for keywords and display any matches.  See apropos(1) for details.

       -K, --global-apropos
              Search for text in all manual pages.  This is a brute-force search, and is likely to take some time; if you can, you should specify a sec‐
              tion to reduce the number of pages that need to be searched.  Search terms may be simple strings (the default), or regular expressions  if
              the --regex option is used.
~~~
so in here I learnt that the -k argument can be used to display some info about some specific keywords or text.
So by learning that I used displayed the manual of apropos and passed man apropos flag which displayed nothing useful, but then I tried man -k flag which did the trick.
It displayed me the following data:
~~~
bash
man -k flag
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
hhzabvendj (1)       - print the flag!
i386 (8)             - change reported architecture in new program environment and/or set personality flags
ioctl_iflags (2)     - ioctl() operations for inode flags
linux32 (1)          - change reported architecture in new program environment and/or set personality flags
linux64 (1)          - change reported architecture in new program environment and/or set personality flags
pcap-config (1)      - write libpcap compiler and linker flags to standard output
security_compute_av_flags (3) - query the SELinux policy database in the kernel
security_compute_av_flags_raw (3) - query the SELinux policy database in the kernel
set_matchpathcon_flags (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking a...
set_matchpathcon_invalidcon (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity check...
set_matchpathcon_printf (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking ...
setarch (1)          - change reported architecture in new program environment and/or set personality flags
setarch (8)          - change reported architecture in new program environment and/or set personality flags
x86_64 (8)           - change reported architecture in new program environment and/or set personality flags
~~~
this made me realize that I had to go through the manual of hhzabvendj command and look for some kind of clues regarding the flag.
Used the following command:
~~~
hacker@man~searching-for-manuals:~$ man hhzabvendj

CHALLENGE(1)                                                       Challenge Commands                                                       CHALLENGE(1)

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

       --hhzabv NUM
              print the flag if NUM is 891

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                             May 2024                                                            CHALLENGE(1)
~~~
Through this I got to know that I had to invoke the --hhzabv argument and pass 891 in front of it to recieve the flag as done in a previous question.
Did that and got the flag.
~~~
bash
hacker@man~searching-for-manuals:~$ /challenge/challenge --hhzabv 891
Correct usage! Your flag: pwn.college{8hhz9LU18a78bv9Q9Me1E23nN92.dZTM4QDL5AjN0czW}
~~~



## Helpful Programs
learnt about the --help argument in this module.
it basically tells us how to run a specific argument or how to invoke it.
so I basically did the following:
~~~
bash
 cd /
hacker@man~helpful-programs:/$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:/$ /challenge/challenge -g
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: expected one argument
hacker@man~helpful-programs:/$ /challenge/challenge -g/--give-the-flag
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: invalid int value: '/--give-the-flag'
hacker@man~helpful-programs:/$ /challenge/challenge -p
The secret value is: 428
hacker@man~helpful-programs:/$ /challenge/challenge -g/428
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
hacker@man~helpful-programs:/$ /challenge/challenge -g 428
Correct usage! Your flag: pwn.college{4hj_mdR28_SRNflFEag3zQuVvi9.ddjM4QDL5AjN0czW}
~~~

## Help for Builtins
learnt about builtins which arent man programs but are built in the shell itself, these are invoked in a way similar to that of commands but the shell handles these builtins internally and doesnt launch other programs.
So in this module I was required to open a builtin with the help command, challenge was supposed to be open with the help command.
~~~
bash
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "QD39iCUN".
hacker@man~help-for-builtins:~$ cd /
hacker@man~help-for-builtins:/$ /challenge/challenge --secret VALUE QD39iCUN
ssh-entrypoint: /challenge/challenge: No such file or directory
hacker@man~help-for-builtins:/$ /challenge/challenge --secretQD39iCUN
ssh-entrypoint: /challenge/challenge: No such file or directory
hacker@man~help-for-builtins:/$ /challenge --secret QD39iCUN
ssh-entrypoint: /challenge: Is a directory
hacker@man~help-for-builtins:/$ /challenge --fortune
ssh-entrypoint: /challenge: Is a directory
hacker@man~help-for-builtins:/$ challenge --fortune
Sorry for mailing this article, I've obviously made a typo (168!=186)
that's the price for being up all night and doing some "quick"
checks before you go to bed ....
                -- Herbert Rosmanith <herp@wildsau.idv.uni-linz.ac.at>
hacker@man~help-for-builtins:/$ challenge --secret QD39iCUN
Correct! Here is your flag!
~~~
as you can see above i tried some standard commands but it worked in the end because I just had to invoke the challenge file which was inside / directory.


