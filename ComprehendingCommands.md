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
~~~

## listing files
in this module, I learnt about the ls command which basically lists all the files inside some directory.
As the module said it had renamed /challenge/run with some random name.
I have to run the /challenge command and list all the files inside it to find the new name of the file.
To do this task firstly I changed my directory to /challenge as instructed in the module using the cd command.
Then I try and read all the files inside the cwd which gives me the following result ----->  27875-renamed-run-20593  DESCRIPTION.md
Now, I didnt understand the result completely as I thought it would just provide me with the list of the files which might or might not contain the flag but no that was not the case.
Then I tried reading the Description.md file using the cat command but that was useless as it just gave me the following output:

~~~
bash
hacker@commands~listing-files:/challenge$ cat DESCRIPTION.md
So far, we've told you which files to interact with.
But directories can have lots of files (and other directories) inside them, and we won't always be here to tell you their names.
You'll need to learn to **l**i**s**t their contents using the `ls` command!

`ls` will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided.
Observe:

```console
hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$
```

In this challenge, we've named `/challenge/run` with some random name!
List the files in `/challenge` to find it.
~~~

After this, I thought of running the renamed file which I got above when I used the ls command but I wasnt sure on how to do so.
So I used a reference video on youtube on how to open a file -----> https://www.youtube.com/watch?v=-ULcwdaEegY&ab_channel=SagarS
I realized after watching the video that I just had to open it using the explicit relative path method which was specifically placing a . before referring to a file and opening it through /
Then I opened the file using this method and voila it worked and gave me the flag.

~~~
bash
hacker@commands~listing-files:/challenge$ ./27875-renamed-run-20593
Yahaha, you found me! Here is your flag:
pwn.college{YlkKAWVF1oEoqNmsuKoqDMu9GQo.dhjM4QDL5AjN0czW}
~~~

## touching files
In this specifc module, I learnt how to touch a file or in other words basically adding a file inside of a directory using the touch command.
The sample command decleration can be found inside the code below.
The module instructed me to create  two files inside of the tmp directory, hence I simply changed my directory to tmp by using the cd command.
Then once my directory was changed I created the two files using the touch command, pwn and college.
Once those were created I ran the /challenge/run and it gave me the flag.
Also I used the ls command once I obtained the flag and it showed me both the files created by me hence they were successfully created.
~~~
bash
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{wmr_lq4jGDt1fsfV69Mph_BGct0.dBzM4QDL5AjN0czW}
hacker@commands~touching-files:/tmp$ ls
bin  college  hsperfdata_root  pwn  tmp.XvrUsDZh8M
~~~

## removing files
This module in contrary to the last module, taught me how to remove a file from a directory using the rm command.
The module instructed me that there is delete_me file inside the home directory and I need to remove it using the rm command and then run the /challenge/check command to check if it was successfully removed or not.
So I just did that, firstly removed the file then run the command and it gave me the flag.
~~~
bash
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{MI38Sct3HkLblHNcA9I8NONzIYS.dZTOwUDL5AjN0czW}
~~~

## hidden files
This module told me about a very important property or characteristic of linux, which is that the ls command which is used to list all the files, does not show the hidden files by default.
A hidden file can be created by using the touch command and by using a . infront of the file name.
For example lets say I type touch college, it would create a file with the name of college which wont be hidden and will be simply displayed by using the ls command.
But if I type touch .college, then it would create a hidden file which wont show up by simply using the ls command and some addition is necessary.
The addition is that -a has to be added in front of the ls command to display all the files including the hidden ones.
Now after learning this I went back to the module and it had instructed me to that a hidden file has been created inside of the directory ./
so, firstly I changed my directory by using the cd command to ./
Once I was in the cwd, I used the ls -a command to display all the files including the hidden ones.
This gave me a file with the name of .flag-11031127937, and then I used the cat command to read its contents.
This gave me the flag.

~~~
bash
ls
Desktop  delete_me  e
hacker@commands~hidden-files:~$ cd /.
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv         bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-11031127937  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cat .flag-11031127937
pwn.college{s8JZErCy2HboJJizefWUszoIFsM.dBTN4QDL5AjN0czW}
~~~



