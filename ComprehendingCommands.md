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
