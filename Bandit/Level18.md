# Level 18
Now when I try to login to level 18, it logs me out and so I read the website and it tells me that .bashrc has been modified and so I cant login.
so that is when I invoke the man ssh command to try and get more info on how to login with some different options and maybe do something different.
reading the manual page of ssh i got to know -t argument can be used to force a pseudo-terminal allocation which it might not log me out of.
did that but it still logged me out of the level.
this was happening as I was still logging in the default shell.
so to fix that i added a /bin/sh at the end of the command I entered so I enter the sh shell and not the default one and this actually prevented me from getting logged out.
did this and could actually cat the readme file now and got the password for the next level.
~~~
 ssh -t bandit18@bandit.labs.overthewire.org -p 2220 /bin/sh
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password:
$ ls
readme
$ cat readme
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
~~~
