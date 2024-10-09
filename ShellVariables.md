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
