# Level 5
in this level I was told that there would be a file inside a folder and given some properties, so I started searching.
using the xargs argument was useless here as alot of files were human readable in here, so I had to surf the net and had to search what was the command for finding a file with a specific size, got to know about the command which was find -size and got the file.
~~~
bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit4@bandit.labs.overthewire.org's password:

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ ls -alps
total 48
4 drwxr-xr-x 2 root    root    4096 Sep 19 07:08 ./
4 drwxr-xr-x 3 root    root    4096 Sep 19 07:08 ../
4 -rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file00
4 -rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file01
4 -rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file02
4 -rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file03
4 -rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file04
4 -rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file05
4 -rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file06
4 -rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file07
4 -rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file08
4 -rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file09
bandit4@bandit:~/inhere$ cat file00
cat: file00: No such file or directory
bandit4@bandit:~/inhere$ cat -file00
cat: invalid option -- 'f'
Try 'cat --help' for more information.
bandit4@bandit:~/inhere$ find  . -type f | xargs file
./-file08: data
./-file02: data
./-file09: data
./-file01: data
./-file00: data
./-file05: data
./-file07: ASCII text
./-file03: data
./-file06: data
./-file04: data
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
bandit4@bandit:~/inhere$ exit
logout
Connection to bandit.labs.overthewire.org closed.
saps@LAPTOP-KKUS7K8J:~$ ssh bandit5@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit5@bandit.labs.overthewire.org's password:

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
bandit5@bandit:~/inhere$ ls -alps
total 88
4 drwxr-x--- 22 root bandit5 4096 Sep 19 07:08 ./
4 drwxr-xr-x  3 root root    4096 Sep 19 07:08 ../
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere00/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere01/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere02/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere03/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere04/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere05/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere06/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere07/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere08/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere09/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere10/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere11/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere12/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere13/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere14/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere15/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere16/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere17/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere18/
4 drwxr-x---  2 root bandit5 4096 Sep 19 07:08 maybehere19/
bandit5@bandit:~/inhere$ find  . -type f | xargs file
./maybehere02/.file1: ASCII text, with very long lines (6350)
./maybehere02/-file1: ASCII text, with very long lines (3800)
./maybehere02/spaces: cannot open `./maybehere02/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere02/-file3: data
./maybehere02/-file2: X1 archive data
./maybehere02/.file2: ASCII text, with very long lines (2576)
./maybehere02/spaces: cannot open `./maybehere02/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere02/spaces: cannot open `./maybehere02/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere02/.file3: data
./maybehere19/.file1: ASCII text, with very long lines (7208)
./maybehere19/-file1: ASCII text, with very long lines (6301)
./maybehere19/spaces: cannot open `./maybehere19/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere19/-file3: data
./maybehere19/-file2: ASCII text, with very long lines (5593)
./maybehere19/.file2: ASCII text, with very long lines (4739)
./maybehere19/spaces: cannot open `./maybehere19/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere19/spaces: cannot open `./maybehere19/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere19/.file3: Dyalog APL version -115.21
./maybehere08/.file1: ASCII text, with very long lines (8168)
./maybehere08/-file1: ASCII text, with very long lines (1076)
./maybehere08/spaces: cannot open `./maybehere08/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere08/-file3: data
./maybehere08/-file2: ASCII text, with very long lines (3824)
./maybehere08/.file2: ASCII text, with very long lines (746)
./maybehere08/spaces: cannot open `./maybehere08/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere08/spaces: cannot open `./maybehere08/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere08/.file3: data
./maybehere15/.file1: ASCII text, with very long lines (2158)
./maybehere15/-file1: ASCII text, with very long lines (8793)
./maybehere15/spaces: cannot open `./maybehere15/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere15/-file3: data
./maybehere15/-file2: ASCII text, with very long lines (9498)
./maybehere15/.file2: ASCII text
./maybehere15/spaces: cannot open `./maybehere15/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere15/spaces: cannot open `./maybehere15/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere15/.file3: data
./maybehere03/.file1: ASCII text, with very long lines (9768)
./maybehere03/-file1: ASCII text, with very long lines (314)
./maybehere03/spaces: cannot open `./maybehere03/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere03/-file3: data
./maybehere03/-file2: ASCII text, with very long lines (6594)
./maybehere03/.file2: ASCII text, with very long lines (8879)
./maybehere03/spaces: cannot open `./maybehere03/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere03/spaces: cannot open `./maybehere03/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere03/.file3: data
./maybehere01/.file1: Clarion Developer (v2 and above) memo data
./maybehere01/-file1: ASCII text, with very long lines (6027)
./maybehere01/spaces: cannot open `./maybehere01/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere01/-file3: data
./maybehere01/-file2: ASCII text
./maybehere01/.file2: ASCII text, with very long lines (3069)
./maybehere01/spaces: cannot open `./maybehere01/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere01/spaces: cannot open `./maybehere01/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere01/.file3: data
./maybehere00/.file1: ASCII text, with very long lines (550)
./maybehere00/-file1: ASCII text, with very long lines (1038)
./maybehere00/spaces: cannot open `./maybehere00/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere00/-file3: OpenPGP Secret Key
./maybehere00/-file2: ASCII text, with very long lines (9387)
./maybehere00/.file2: ASCII text, with very long lines (7835)
./maybehere00/spaces: cannot open `./maybehere00/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere00/spaces: cannot open `./maybehere00/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere00/.file3: data
./maybehere12/.file1: ASCII text, with very long lines (5814)
./maybehere12/-file1: ASCII text, with very long lines (9677)
./maybehere12/spaces: cannot open `./maybehere12/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere12/-file3: data
./maybehere12/-file2: ASCII text
./maybehere12/.file2: ASCII text, with very long lines (8243)
./maybehere12/spaces: cannot open `./maybehere12/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere12/spaces: cannot open `./maybehere12/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere12/.file3: data
./maybehere17/.file1: ASCII text, with very long lines (894)
./maybehere17/-file1: ASCII text, with very long lines (1132)
./maybehere17/spaces: cannot open `./maybehere17/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere17/-file3: data
./maybehere17/-file2: ASCII text, with very long lines (1790)
./maybehere17/.file2: ASCII text, with very long lines (8340)
./maybehere17/spaces: cannot open `./maybehere17/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere17/spaces: cannot open `./maybehere17/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere17/.file3: data
./maybehere05/.file1: ASCII text, with very long lines (3200)
./maybehere05/-file1: ASCII text, with very long lines (2345)
./maybehere05/spaces: cannot open `./maybehere05/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere05/-file3: OpenPGP Public Key
./maybehere05/-file2: ASCII text, with very long lines (5958)
./maybehere05/.file2: ASCII text, with very long lines (5916)
./maybehere05/spaces: cannot open `./maybehere05/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere05/spaces: cannot open `./maybehere05/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere05/.file3: data
./maybehere09/.file1: ASCII text, with very long lines (6762)
./maybehere09/-file1: ASCII text, with very long lines (3627)
./maybehere09/spaces: cannot open `./maybehere09/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere09/-file3: data
./maybehere09/-file2: ASCII text, with very long lines (773)
./maybehere09/.file2: ASCII text, with very long lines (8516)
./maybehere09/spaces: cannot open `./maybehere09/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere09/spaces: cannot open `./maybehere09/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere09/.file3: data
./maybehere06/.file1: ASCII text, with very long lines (1270)
./maybehere06/-file1: ASCII text, with very long lines (5730)
./maybehere06/spaces: cannot open `./maybehere06/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere06/-file3: data
./maybehere06/-file2: ASCII text, with very long lines (1075)
./maybehere06/.file2: ASCII text, with very long lines (8975)
./maybehere06/spaces: cannot open `./maybehere06/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere06/spaces: cannot open `./maybehere06/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere06/.file3: data
./maybehere10/.file1: ASCII text, with very long lines (7091)
./maybehere10/-file1: ASCII text, with very long lines (1051)
./maybehere10/spaces: cannot open `./maybehere10/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere10/-file3: data
./maybehere10/-file2: ASCII text, with very long lines (1990)
./maybehere10/.file2: ASCII text
./maybehere10/spaces: cannot open `./maybehere10/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere10/spaces: cannot open `./maybehere10/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere10/.file3: data
./maybehere11/.file1: ASCII text, with very long lines (451)
./maybehere11/-file1: ASCII text, with very long lines (1210)
./maybehere11/spaces: cannot open `./maybehere11/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere11/-file3: data
./maybehere11/-file2: ASCII text, with very long lines (4558)
./maybehere11/.file2: ASCII text, with very long lines (2500)
./maybehere11/spaces: cannot open `./maybehere11/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere11/spaces: cannot open `./maybehere11/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere11/.file3: data
./maybehere07/.file1: ASCII text, with very long lines (3064)
./maybehere07/-file1: ASCII text, with very long lines (3662)
./maybehere07/spaces: cannot open `./maybehere07/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere07/-file3: data
./maybehere07/-file2: ASCII text, with very long lines (2487)
./maybehere07/.file2: ASCII text, with very long lines (1000)
./maybehere07/spaces: cannot open `./maybehere07/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere07/spaces: cannot open `./maybehere07/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere07/.file3: OpenPGP Public Key
./maybehere14/.file1: ASCII text, with very long lines (3426)
./maybehere14/-file1: ASCII text, with very long lines (4281)
./maybehere14/spaces: cannot open `./maybehere14/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere14/-file3: OpenPGP Secret Key
./maybehere14/-file2: ASCII text, with very long lines (8350)
./maybehere14/.file2: ASCII text, with very long lines (1502)
./maybehere14/spaces: cannot open `./maybehere14/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere14/spaces: cannot open `./maybehere14/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere14/.file3: data
./maybehere04/.file1: ASCII text, with very long lines (2439)
./maybehere04/-file1: ASCII text, with very long lines (4409)
./maybehere04/spaces: cannot open `./maybehere04/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere04/-file3: data
./maybehere04/-file2: ASCII text, with very long lines (2618)
./maybehere04/.file2: ASCII text, with very long lines (6143)
./maybehere04/spaces: cannot open `./maybehere04/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere04/spaces: cannot open `./maybehere04/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere04/.file3: data
./maybehere13/.file1: ASCII text, with very long lines (5257)
./maybehere13/-file1: ASCII text, with very long lines (1358)
./maybehere13/spaces: cannot open `./maybehere13/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere13/-file3: data
./maybehere13/-file2: ASCII text, with very long lines (1422)
./maybehere13/.file2: ASCII text, with very long lines (8951)
./maybehere13/spaces: cannot open `./maybehere13/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere13/spaces: cannot open `./maybehere13/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere13/.file3: data
./maybehere18/.file1: ASCII text, with very long lines (5701)
./maybehere18/-file1: ASCII text, with very long lines (9696)
./maybehere18/spaces: cannot open `./maybehere18/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere18/-file3: data
./maybehere18/-file2: ASCII text
./maybehere18/.file2: ASCII text, with very long lines (2083)
./maybehere18/spaces: cannot open `./maybehere18/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere18/spaces: cannot open `./maybehere18/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere18/.file3: data
./maybehere16/.file1: ASCII text, with very long lines (5425)
./maybehere16/-file1: ASCII text, with very long lines (4276)
./maybehere16/spaces: cannot open `./maybehere16/spaces' (No such file or directory)
file1:                cannot open `file1' (No such file or directory)
./maybehere16/-file3: data
./maybehere16/-file2: ASCII text, with very long lines (5300)
./maybehere16/.file2: ASCII text, with very long lines (8471)
./maybehere16/spaces: cannot open `./maybehere16/spaces' (No such file or directory)
file3:                cannot open `file3' (No such file or directory)
./maybehere16/spaces: cannot open `./maybehere16/spaces' (No such file or directory)
file2:                cannot open `file2' (No such file or directory)
./maybehere16/.file3: DOS executable (COM), start instruction 0x8cfa2314 44ee920f
bandit5@bandit:~/inhere$ cat ./maybehere00
cat: ./maybehere00: Is a directory
bandit5@bandit:~/inhere$ cat ./maybehere00/-file1
WRswI03L5YXDJ3oVnNL9akOOZciJTjH8ZzqniOAqdfDHUQnxtwk6QOfrFacgVEvhzlY9d0VI0mo05vQYDCWjVMkR9ZVuXVxOVmeizUr4BQyYKaFjcxYoB5BryUBvd45xN2aPOkErEbKHWNnaYOtnbsHkRCiDeQvKm39mU3RUS1dqU4BaNwNmnNQxVqGFDc40UukmwXiuZkzADnNk5YpEYuheTBuIXRefSalkLQkXs7kyxiD0Q24SqEYwZuZ9RVNEuXM64YrIJa8ZPcLDJtdIymipP1clhFLzTtV1Eh7ZjdC17o7bDZKEiD2iQKkp73UmNypnYgxMhbUOLmDpit2dJHbEsiQNNN7kDe2DSBhiBRW3jxCzqJmkPM8bkxIOl4vrjuuZOsD51JgTL9njPrp6EhSciYh0oA9flulzuo2GC3HM0DDK4GoKlpkvmVsDCtJwGCN8Q7aSVdtEWc2JbF5YuhGouWqKdvH6RTMlpO7ETqj5MJAyMZEtfr4jmXEtM5qzQjQuPdbAdoTVb3asp8bONM7yTLq13DRWhxnQYiJXDHcCqxUTbw8AJ4MvUbMJnIahkswv6NJsuWtaoQGuyHzPGAabmrRQNvKtZbwNBfojltOVNjvGDc1IPDE5OsFsR8uCXNQ5SUqmUhtLZgVftqtDD6Mppcj5gaeRXFrqIblkM5W710qcPlQkDKKHeWBpYcpFGr4kQTt0OIrEyPTV49qEhJuE0H8Hip5B8ALvY40O4RqvJyQvvA4eRIkudoLmqh4DGH3JZHIbsLqgWhUbKthMAjpvFnwaXkoMigDzIOJf5BTCJu7gCJRnA6t4mDUFNVSlMbHqGF2t3GrzpqjY4JHhdTvVQcJc898wZSJiCbUvahWtRQkMB21SdFPSQqe7KKAD31TRWt510ncw81yJHtIZaIVIrsIEmc0DLURkLM6NXYp65aVdSJhlPuLHxqzVpEThHutC7h4Ivq6DV2vJz4GCJxP7JYOGMgBDJRydHrI0B93fPZA8JKQlEkHtAsO61c969JEtDdXvgutTg9
bandit5@bandit:~/inhere$ find -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
~~~
