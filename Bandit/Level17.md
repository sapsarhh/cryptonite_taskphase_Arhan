# Level 17
Finally the connection and porting levels ended good god.
Now finally something new.
Leant about the diff command and its use.
basically used to compare two files text by text and give the output for whatever text it finds different.
reading the man page and using --help with the diff command taught me how to use it so I used it and got the password.
~~~
bash
bandit17@bandit:~$ ls
passwords.new  passwords.old
bandit17@bandit:~$ cat passwords.new | grep | passwords.old | diff
Usage: grep [OPTION]... PATTERNS [FILE]...
Try 'grep --help' for more information.
diff: missing operand after 'diff'
diff: Try 'diff --help' for more information.
passwords.old: command not found
bandit17@bandit:~$ man diff
bandit17@bandit:~$ diff --help
Usage: diff [OPTION]... FILES
Compare FILES line by line.

Mandatory arguments to long options are mandatory for short options too.
      --normal                  output a normal diff (the default)
  -q, --brief                   report only when files differ
  -s, --report-identical-files  report when two files are the same
  -c, -C NUM, --context[=NUM]   output NUM (default 3) lines of copied context
  -u, -U NUM, --unified[=NUM]   output NUM (default 3) lines of unified context
  -e, --ed                      output an ed script
  -n, --rcs                     output an RCS format diff
  -y, --side-by-side            output in two columns
  -W, --width=NUM               output at most NUM (default 130) print columns
      --left-column             output only the left column of common lines
      --suppress-common-lines   do not output common lines

  -p, --show-c-function         show which C function each change is in
  -F, --show-function-line=RE   show the most recent line matching RE
      --label LABEL             use LABEL instead of file name and timestamp
                                  (can be repeated)

  -t, --expand-tabs             expand tabs to spaces in output
  -T, --initial-tab             make tabs line up by prepending a tab
      --tabsize=NUM             tab stops every NUM (default 8) print columns
      --suppress-blank-empty    suppress space or tab before empty output lines
  -l, --paginate                pass output through 'pr' to paginate it

  -r, --recursive                 recursively compare any subdirectories found
      --no-dereference            don't follow symbolic links
  -N, --new-file                  treat absent files as empty
      --unidirectional-new-file   treat absent first files as empty
      --ignore-file-name-case     ignore case when comparing file names
      --no-ignore-file-name-case  consider case when comparing file names
  -x, --exclude=PAT               exclude files that match PAT
  -X, --exclude-from=FILE         exclude files that match any pattern in FILE
  -S, --starting-file=FILE        start with FILE when comparing directories
      --from-file=FILE1           compare FILE1 to all operands;
                                    FILE1 can be a directory
      --to-file=FILE2             compare all operands to FILE2;
                                    FILE2 can be a directory

  -i, --ignore-case               ignore case differences in file contents
  -E, --ignore-tab-expansion      ignore changes due to tab expansion
  -Z, --ignore-trailing-space     ignore white space at line end
  -b, --ignore-space-change       ignore changes in the amount of white space
  -w, --ignore-all-space          ignore all white space
  -B, --ignore-blank-lines        ignore changes where lines are all blank
  -I, --ignore-matching-lines=RE  ignore changes where all lines match RE

  -a, --text                      treat all files as text
      --strip-trailing-cr         strip trailing carriage return on input

  -D, --ifdef=NAME                output merged file with '#ifdef NAME' diffs
      --GTYPE-group-format=GFMT   format GTYPE input groups with GFMT
      --line-format=LFMT          format all input lines with LFMT
      --LTYPE-line-format=LFMT    format LTYPE input lines with LFMT
    These format options provide fine-grained control over the output
      of diff, generalizing -D/--ifdef.
    LTYPE is 'old', 'new', or 'unchanged'.  GTYPE is LTYPE or 'changed'.
    GFMT (only) may contain:
      %<  lines from FILE1
      %>  lines from FILE2
      %=  lines common to FILE1 and FILE2
      %[-][WIDTH][.[PREC]]{doxX}LETTER  printf-style spec for LETTER
        LETTERs are as follows for new group, lower case for old group:
          F  first line number
          L  last line number
          N  number of lines = L-F+1
          E  F-1
          M  L+1
      %(A=B?T:E)  if A equals B then T else E
    LFMT (only) may contain:
      %L  contents of line
      %l  contents of line, excluding any trailing newline
      %[-][WIDTH][.[PREC]]{doxX}n  printf-style spec for input line number
    Both GFMT and LFMT may contain:
      %%  %
      %c'C'  the single character C
      %c'\OOO'  the character with octal code OOO
      C    the character C (other characters represent themselves)

  -d, --minimal            try hard to find a smaller set of changes
      --horizon-lines=NUM  keep NUM lines of the common prefix and suffix
      --speed-large-files  assume large files and many scattered small changes
      --color[=WHEN]       color output; WHEN is 'never', 'always', or 'auto';
                             plain --color means --color='auto'
      --palette=PALETTE    the colors to use when --color is active; PALETTE is
                             a colon-separated list of terminfo capabilities

      --help               display this help and exit
  -v, --version            output version information and exit

FILES are 'FILE1 FILE2' or 'DIR1 DIR2' or 'DIR FILE' or 'FILE DIR'.
If --from-file or --to-file is given, there are no restrictions on FILE(s).
If a FILE is '-', read standard input.
Exit status is 0 if inputs are the same, 1 if different, 2 if trouble.

Report bugs to: bug-diffutils@gnu.org
GNU diffutils home page: <https://www.gnu.org/software/diffutils/>
General help using GNU software: <https://www.gnu.org/gethelp/>
bandit17@bandit:~$ cat passwords.new | grep | passwords.old | diff -a
Usage: grep [OPTION]... PATTERNS [FILE]...
Try 'grep --help' for more information.
diff: missing operand after '-a'
diff: Try 'diff --help' for more information.
passwords.old: command not found
bandit17@bandit:~$ cat passwords.new | passwords.old | diff -a
diff: missing operand after '-a'
diff: Try 'diff --help' for more information.
passwords.old: command not found
bandit17@bandit:~$ cat passwords.new | passwords.old | diff
diff: missing operand after 'diff'
diff: Try 'diff --help' for more information.
passwords.old: command not found
bandit17@bandit:~$ cat passwords.new
BTrrmkKVXra01wWzxqzFmAMY9CbPXRlc
zxYJ8Detw68SBZluYcJzAkEwrwPB1uCh
J1mJLnxroUUJC5YEtfHVPq6LXxkWTbsF
oSRyw7ANImF3fjwvjAnKqcJgL37Eltmf
efslUmsn2iMnYngpaChSBe7JGgrdl1SJ
cWqaMSNyS06Ls5p5FL6xWBiafm1WR4js
jtFnBY4XzzHQVjT4NYwBZka2fRuNB40z
wyuE9cNn7ruxWvJx39lzJsiakMVoiaAL
viWro0rDldjuIhMbtuYqwpuEq11KQ1Dk
GSJ2XOnI3OW6Kz3Bcu8jEWPldxxZYtwV
Y9L7A4xLtKse8Qsv4cVOnkuxcJlTMnwx
QsXRjG6uAMGD4UaxOX9dNjW9ZBIARt0b
8z2wzuSn0FSW3Kd43n0rX574g8aIhpeP
bIsJ24EaCpslmVSk8PYRQ6I3JzE24CU2
BL96qzomBra296hGG95IL2EJVHhtCxnR
sBJvUThUpq58L5MfP3xBtqAg07iqxFNo
breOHXDOaU6pSVtwtnqoDvB0eBHIzQNz
Hyri3fE6PElDCAzxXmYjcIYPDm1GQq1N
nPMnwp6BWPZwFMXYRIYr0sYyeoRX7OkB
fGD6FhO55K1tlaqzivxmlv2TxKuouCQ9
VYsYVJYhPIrMvPhR947eEyFDAUcC8qAY
X96s0ctaz9jKBbBZXEVZjCRg71RPi30o
Hm7YpVTbNYnax2JNH7t0wpeNtmZaur66
JU8pvHxM7hpNA4xf9fGN8zGczvciZ4rF
PCe8KFcLPad79DRPjh1oR3MOzOeCkWHZ
hAsIkoS2h0kaFPOreW6va8zuGE7FfaeG
3HkS70idKGkDaSdiZKxsEJfNwN6bB44C
4IomZJlt4oZVdUMe3P709ibJMMGgKVVa
o3SVmlinHtOGkYx2OUcMdWNFpcnfR9GI
A6mgj41YOCD6Ln5duYzGskRPX7BNGdWP
Wio8CxULxerO0mVK9XqS7CzPEqhvkVTI
RBteFXN1lcmtjaHlf9MQBd2Tw6COnxnl
6WFx7rBYDHS0cbtC6I3SgFC48Mus97gT
cUCapF3fmt1xWL1KYOcE2hHcHR9acLWK
OtnNexZjXd8SOY2c9PJonN8Kt9r1YacT
9TuAz9N69hhOF0mJvkwZ62jwDZhSMYdX
jHUGSWtCiBmW3EhB83uHvqSdCSPzLoSp
NUahNZOPpVYgBeA3sxTSloUHCCNbmIcE
Udq1Zw8oOdLjcLZSoWFb3XVsLVr2J7e7
fwJjyJfLsqI7eA3q1pmW0WjptEJPyjVj
9jbIrrT9OlPADZDBfF1UOoz4lhboOnsT
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
dX464MV2LHPWYN9RDa7AnVBqsxjl1zui
GOTGHQIZKu2qwhUTibu5PQaMEMWvoUDR
t7szZtdGClutCs1g4uWKN5I1oV3cnA0c
UjvLtH0PwVCMVKin557N52aHiyl0kYq1
nlgqcBzlhJ2VviwtRrQ5uWchvklbT4pP
7e9nLN3c67bDY2xu3WyJHEwV7nYdvGPE
ExgTqIHbr2ns16kLsqyajBZkjMQLTViV
G9cfTflYTtWolu6icsXkQub5CVDZUthf
z2EA6BCZxLAQfYjWeAEkY1KiO2govaZb
denuyi6K0zLwrBJ7bhK6HBcEWx5Q3pZU
DTQZOhhW6BAOv8xsl7cNJWrE3xUpyVuZ
PzkdBqvSfbrXDccTZoOTMvPv3g62uht2
qsCnO2xNgscH1kEPY0x9bbWW4wqhuKun
BXeAlHizeskRwL8DBU1pkuRNf8YQs1fy
JbjSP4bawPjhVblhIKvYsa6DSrQ0K8Pa
mLN3ZguwRodFz1ff9212diaWRG38JmP8
VEvQa0rdLpnWuXdBizNHDHOoNBUOji2v
H7pLihoyQyokYMNsblaQRZDSbJOeUN1M
zSLn2YysyQ72CxOmuLxOjSDob3z5rfhw
7lAgyTUFK10KM4bddgRRw56IJmTSHGkJ
kWLg9LHTHWvwyHVchjfjvsl56NKyL6lj
GFHzOC2d1AFDbuX4CN1ENUOtIgyDIKJt
1Gx2ud8nXUZOTv7xmJUeRj13y4rLyya6
B6SjgQEqvhiocLV1yvM0pjX7IdlsiCH5
3P7gn1Bc6XZUK6ztLfnGWcbeG7YHiHiI
nFec0Ku80ZdvtGCxoPB5cttTESXpKQnQ
1jhfUAWYdazPlD4SP5YVWKeiw0wOq5Ri
WNfLXhuLdvvSr7ZLevsEr4cO3NvPG490
BJFMpf1KbAs8EyqOkarPvKemHRV8tZEh
c0ym4wfyWFBJDpf5GijAdD9ztGOxNlhV
Ch6fjISjwwgUp1TbZTYuXGNTA8FLdYrv
KUMiMhP2oU7vgY9TX4YEne7rbX8yFUZn
tI64dQ5Tk7UNjE2D6nG9BplQFogtmCGO
WfPpHSJPVR0bbanzbX1CnjuIex4K10D6
JINaeqrYEhqrzxMCvGbmofyb36GNfFiC
4tgIAcfwRpPJSlaOWU3rDPn8yMG077hI
1nRRyyOmXFR6ArHTKwuoQ92qoSc4VdQT
Rl0ov5T2JPrTTgk56ogS1GTMwQ0vmoiE
94X0gWlDT3wuXeB6v86U7kiHWOsVtiQt
fRj0kPfYCkK8qEkpQp7aChL3BbyikcuF
rudgpHLFpYtWFHhFjmtNtUZLT9F1tGqn
osVZo4VuRGRZ94Op1IpcLub1ljo5Scig
pX8Knc9zUufKCuAWt0xrQ0lBXccURT9y
SszksMS8Rgtsn0bwFmuEeIQVBQakwmdB
BXwQooIJThMQlgLCcvI1MVRXeqogZvbT
eJyAXFSdnbnPlhCAPmNFQkiZ0KCxetCz
HWYjo80dF1HCZlVm8KSfyIjjhWxkPGBl
GBO5mHleMNnEUxbxEMyt9exwDUbPbOH4
YqjE5WimoXL4xfXCZfSdwUS3u5azCZ3s
751nXWjzPrlYjehtBSRAxQQ72QUM3XLF
MgrEjWdEmIzbjOsWrr5CPzGUCkEDzozZ
of7XKBKAukCSlCkTaGSXmaRipODqq5Dm
ybshx1FNxqzADl7bpkm5gttCFtUy1zJX
MWUhEo0IaOxdHaHdwHlAA9Uc5XnCnitH
REUKNmW9j1fmX8hhoq3UmGwOX0uazs0L
IL4T25H4ZPoByaPzGTofsozMg03BvjI4
MSmRC2afxQDbU8F3eJuSQiXfxJRMN3oH
Q7k1gkA8CAmEqwMOMWtzAXxXTSjK1omj
bandit17@bandit:~$ diff passwords.new passwords.old
42c42
< x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
---
> ktfgBvpMzWKR5ENj26IbLGSblgUG9CzB
~~~
