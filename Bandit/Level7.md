# Level 7
in this file I was required to look for the password in the file data.txt and the hint given was that the password was next to the millionth.
so firstly I used the command cat data.txt grep "millionth".
but this gave me literal tons of data which a human cant comb through and find and at the end it told me millionth directory wasnt found, so I realized my mistake and then used the command cat data.txt | grep "millionth" which worked and gave me the password.
~~~
bash
cat data.txt | grep millionth
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
~~~
