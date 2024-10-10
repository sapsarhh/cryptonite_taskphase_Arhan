# Shell Variables
## Printing Variables
Got to know that like programming languages, linux supports variables.
In the module learnt how to print variables using the $ operator which is used to access variables.
in the question I was supposed to access the variable flag using the $ operator and then echo it to display the flag. 
~~~
bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{MX81yys-BcYSEsw3pzmvQbwBgkJ.ddTN1QDL5AjN0czW}
hacker@variables~printing-variables:~$
~~~

## Setting Variables
Learnt that of course like programming languages, values can be assigned to a variable. Can be done using the = operator.
Also learnt that $ isnt used when assigning value to a variable, because $ is strictly used to access or to expand as its called variable expansion.
for example lets say there is a variable cryptonite and I want to assign value learn to it then,
ill have to pass the arguments cryptonite=learn and not $cryptonite=learn which is syntactically wrong.
in the question i was just required to assign value COLLEGE to the PWN variable.
~~~
bash
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{I-aHWb-ikx3aZPasaxORMn7dpBd.dlTN1QDL5AjN0czW}
~~~


## Multi-word Variables
in the module I got to know how to declare and pass a multi word value to a variable. 
This is basically done by using "" and enclosing the value inside "" as giving only a space and no quotes would lead to an error as the next word wont be a command.
So in the following question I was instructed to assign a multi word value to the variable PWN, done so by enclosing the text in double quotes.
~~~
bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{8jQA67n5pfCX6Qw1Uh1B_LWh8XF.dBjN1QDL5AjN0czW}
~~~


## Exporting Variables
first of all learnt about the sh command which is used to make a subshell of the main shell, also the variables created inside the main shell can be exported inside the subshell or the child shell.
after that I learnt about the export command which is used to export the value of one variable inside the main shell into the subshell which cannot be done manually.
lets say I have a variable and I of course call it inside the main shell using $ operator it would return me the value of the variable or the data which is stored inside the variable.
But instead if I use the sh command and inside the subshell I try to access the variable with some data, the variable will not return me the value which it returned inside the main shell, hell it wont return any value.
This is where the export command comes in and can be used to export the data to the child shell as well.
So in the question I had to use the export command the PWN variable and assign the value college to it.
Also I had to assign the value PWN to college but not export it.
Did the following and obtained the flag.

~~~
bash
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{IToOucSW9gqhGytVJbTAmNIds-9.dJjN1QDL5AjN0czW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
~~~


## Printing Exported Variables
learnt the use of env command, which is used to print every exported variable in the shell in contrast to the echo command which can at a time only print one exported variable.
in the question I was required to simply run the env command which would display me the exported variables and flag being part of them will be displayed.
~~~
bash
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
DOJO_AUTH_TOKEN=39da9abbe76885f5bf9a3bcecbe3d9c210358b4511c403295dfa5da52c3925a4
HOME=/home/hacker
LANG=C.UTF-8
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.7z=01;31:*.ace=01;31:*.alz=01;31:*.apk=01;31:*.arc=01;31:*.arj=01;31:*.bz=01;31:*.bz2=01;31:*.cab=01;31:*.cpio=01;31:*.crate=01;31:*.deb=01;31:*.drpm=01;31:*.dwm=01;31:*.dz=01;31:*.ear=01;31:*.egg=01;31:*.esd=01;31:*.gz=01;31:*.jar=01;31:*.lha=01;31:*.lrz=01;31:*.lz=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.lzo=01;31:*.pyz=01;31:*.rar=01;31:*.rpm=01;31:*.rz=01;31:*.sar=01;31:*.swm=01;31:*.t7z=01;31:*.tar=01;31:*.taz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tgz=01;31:*.tlz=01;31:*.txz=01;31:*.tz=01;31:*.tzo=01;31:*.tzst=01;31:*.udeb=01;31:*.war=01;31:*.whl=01;31:*.wim=01;31:*.xz=01;31:*.z=01;31:*.zip=01;31:*.zoo=01;31:*.zst=01;31:*.avif=01;35:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.crdownload=00;90:*.dpkg-dist=00;90:*.dpkg-new=00;90:*.dpkg-old=00;90:*.dpkg-tmp=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:*.swp=00;90:*.tmp=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:
FLAG=pwn.college{MwU1ckV5fxEM-2SpsiepRMC9AhF.dhTN1QDL5AjN0czW}
LESSCLOSE=/usr/bin/lesspipe %s %s
TERM=xterm
LESSOPEN=| /usr/bin/lesspipe %s
SHLVL=1
LC_CTYPE=C.UTF-8
PATH=/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/run/workspace/bin/env
~~~


## Storing Command Output
learnt about command substition, which is directly used to access a file using the $ operator through its file path and then echo that file previously accessed,
to read the content.
In this question I was required to access the run file through its file path and store its content in the PWN variable, then echo the PWN variable to read the flag.


~~~
bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $"PWN"
PWN
hacker@variables~storing-command-output:~$ echo "$PWN"
pwn.college{8XQ0l6vUbAlfnQvJB94iJBcV4ia.dVzN0UDL5AjN0czW}
~~~

## Reading Input
learnt about the read command which is used to read some display from a variable when inputted into that variable.
the echo command cant help here and will be useless as it wont display the input in the variable.
in the question i was required to read the PWN variable, as you can see the echo command didnt work here as it didnt display the data inputted into the variable.
~~~
bash
acker@variables~reading-input:~$ echo "$PWN"

hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{sf1GZV8ODvL3TqK_raUUtLY-7PK.dhzN1QDL5AjN0czW}
~~~

## Reading Files
in this question I was required to read the PWN variable after I have used the command < to stdout the output of /challenge/read_me to the PWN variable.
~~~
bash
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{E5ZK4YggoBalqfZSmzf7EPnv5cc.dBjM4QDL5AjN0czW}
~~~
