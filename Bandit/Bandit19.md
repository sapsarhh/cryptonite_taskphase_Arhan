# Bandit 19
So firstly in the level I had to setuid which i didnt really know the meaning of or how to setup it up.
so I just began with using the ls command.
it displayed me one file which was highlighted in red, meaning the file had special conditions of course.
now when I tried to invoke the file using the ./ operator it told me that I should run the command as another user with some other command such as id.
So I tried the given example and it worked and gave me the desired result.
so I tried the same but now with catting the  bandit19 file but that didnt work so I cat'ed the bandit20 file instead and got the password.
~~~
bandit19@bandit:~$ setuid
Command 'setuid' not found, but can be installed with:
apt install super
Please ask your administrator.
bandit19@bandit:~$ ls
bandit20-do
bandit19@bandit:~$ ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do id
bandit19@bandit:~$ ./bandit20-do id
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
bandit19@bandit:~$ ./bandit20-do ls
bandit20-do
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit19
cat: /etc/bandit_pass/bandit19: Permission denied
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
~~~
