# Chaining Commands
## Chaining with semicolons
Leant about chaining in the linux terminal, which is highly efficient in the sense that 2 or more commands can be written in the same line and executed together.
for this a ; can be used which works the same way as the enter key does.
for example lets say i want to create a file called cryptonite and then read it
normally I would do:
touch cryptonite
cat cryptonite
but instead to make it better I can just do this
touch cryptonite ; cat cryptonite
which would work the same way.
coming to the question, I was required to run the /challenge/college file and invoke the /challenge/pwn in the same line seperated by a semicolon basically chain those two commands
~~~
bash
/challenge/college ; /challenge/pwn
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{gEddEkVTbtwxii-KNR0xK77lDGa.dVTN4QDL5AjN0czW}
~~~

