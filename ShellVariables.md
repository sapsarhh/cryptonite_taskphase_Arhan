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


##
