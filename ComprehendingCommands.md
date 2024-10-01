# Comprehending Commands
## cat: not the pet, but the command!
Learnt about the cat command, which I used in the earlier stages of the setup of pwn to read the contents of key.pub, but finally realized now that it is basically used to read or display the contents of some file.
The module told me to read the contents of the flag file so I used the cat command to read flag and that is basically how I obtained the flag for this module.
Watched the following video to get more information on the cat command: https://www.youtube.com/watch?v=z3nJlyrJYW4&ab_channel=LearnLinuxTV
~~~
bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{oEkX_1qyynT9EgfaKRtpttxJBUb.dFzN1QDL5AjN0czW}
~~~


## catting absolute paths
In this module, I learned how to use the cat command with an absolute path because the last question was just straight out of the home directory.
so as the module said that you have to read the contents of the /flag file i did that, firstly i tried opening the /flag directory but the permission was denied.
so then i just read the contents of cat file using cat /flag and that succesfully worked and gave me the flag.
~~~
bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{I8CQYPOPFcRkw8t4Y4iyVAQ8Gst.dlTM5QDL5AjN0czW}
~~~



## more catting practice
In this module I learnt how to to use the cat command without cd'ing a directory.
Instead of cd'ing I directly used the cat command by using the absolute path wherever that specific file is.
~~~
bash
cat /lib/systemd/ntp-units.d/flag
pwn.college{06cNbnIHOTrEbGxHnFgscOkuMH6.dBjM5QDL5AjN0czW}
~~~

## grepping for a needle in a haystack
Learnt about the grep module which is highly useful as it is used to search for some specific text inside a file. The sample command declaration can be found inside the code. Then after learning what grep does, I followed the instructions of the module and as it says that every flag starts with pwn.college I used that information to search up the text pwn.college inside the specific file and found the flag using the grep command.
~~~
bash
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt pwn.college
/challenge/data.txt:pwn.college{4DhXVBM9Ak9fJgQt-h721KOUGOa.ddTM4QDL5AjN0czW}
