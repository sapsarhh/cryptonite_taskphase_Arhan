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


## catting absolute paths
In this module, I learned how to use the cat command with an absolute path because the last question was just straight out of the home directory.
so as the module said that you have to read the contents of the /flag file i did that, firstly i tried opening the /flag directory but the permission was denied.
so then i just read the contents of cat file using cat /flag and that succesfully worked and gave me the flag.
~~~
bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{I8CQYPOPFcRkw8t4Y4iyVAQ8Gst.dlTM5QDL5AjN0czW}
~~~



## more catting practice
In this module I learnt how to to use the cat command without cd'ing a directory.
Instead of cd'ing I directly used the cat command by using the absolute path wherever that specific file is.
~~~
bash
cat /lib/systemd/ntp-units.d/flag
pwn.college{06cNbnIHOTrEbGxHnFgscOkuMH6.dBjM5QDL5AjN0czW}
~~~

## grepping for a needle in a haystack
Learnt about the grep module which is highly useful as it is used to search for some specific text inside a file. The sample command declaration can be found inside the code. Then after learning what grep does, I followed the instructions of the module and as it says that every flag starts with pwn.college I used that information to search up the text pwn.college inside the specific file and found the flag using the grep command.
~~~
bash
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt pwn.college
/challenge/data.txt:pwn.college{4DhXVBM9Ak9fJgQt-h721KOUGOa.ddTM4QDL5AjN0czW}
~~~

## listing files
in this module, I learnt about the ls command which basically lists all the files inside some directory.
As the module said it had renamed /challenge/run with some random name.
I have to run the /challenge command and list all the files inside it to find the new name of the file.
To do this task firstly I changed my directory to /challenge as instructed in the module using the cd command.
Then I try and read all the files inside the cwd which gives me the following result ----->  27875-renamed-run-20593  DESCRIPTION.md
Now, I didnt understand the result completely as I thought it would just provide me with the list of the files which might or might not contain the flag but no that was not the case.
Then I tried reading the Description.md file using the cat command but that was useless as it just gave me the following output:

~~~
bash
hacker@commands~listing-files:/challenge$ cat DESCRIPTION.md
So far, we've told you which files to interact with.
But directories can have lots of files (and other directories) inside them, and we won't always be here to tell you their names.
You'll need to learn to **l**i**s**t their contents using the `ls` command!

`ls` will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided.
Observe:

```console
hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$
```

In this challenge, we've named `/challenge/run` with some random name!
List the files in `/challenge` to find it.
~~~

After this, I thought of running the renamed file which I got above when I used the ls command but I wasnt sure on how to do so.
So I used a reference video on youtube on how to open a file -----> https://www.youtube.com/watch?v=-ULcwdaEegY&ab_channel=SagarS
I realized after watching the video that I just had to open it using the explicit relative path method which was specifically placing a . before referring to a file and opening it through /
Then I opened the file using this method and voila it worked and gave me the flag.

~~~
bash
hacker@commands~listing-files:/challenge$ ./27875-renamed-run-20593
Yahaha, you found me! Here is your flag:
pwn.college{YlkKAWVF1oEoqNmsuKoqDMu9GQo.dhjM4QDL5AjN0czW}
~~~

## touching files
In this specifc module, I learnt how to touch a file or in other words basically adding a file inside of a directory using the touch command.
The sample command decleration can be found inside the code below.
The module instructed me to create  two files inside of the tmp directory, hence I simply changed my directory to tmp by using the cd command.
Then once my directory was changed I created the two files using the touch command, pwn and college.
Once those were created I ran the /challenge/run and it gave me the flag.
Also I used the ls command once I obtained the flag and it showed me both the files created by me hence they were successfully created.
~~~
bash
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{wmr_lq4jGDt1fsfV69Mph_BGct0.dBzM4QDL5AjN0czW}
hacker@commands~touching-files:/tmp$ ls
bin  college  hsperfdata_root  pwn  tmp.XvrUsDZh8M
~~~

## removing files
This module in contrary to the last module, taught me how to remove a file from a directory using the rm command.
The module instructed me that there is delete_me file inside the home directory and I need to remove it using the rm command and then run the /challenge/check command to check if it was successfully removed or not.
So I just did that, firstly removed the file then run the command and it gave me the flag.
~~~
bash
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{MI38Sct3HkLblHNcA9I8NONzIYS.dZTOwUDL5AjN0czW}
~~~

## hidden files
This module told me about a very important property or characteristic of linux, which is that the ls command which is used to list all the files, does not show the hidden files by default.
A hidden file can be created by using the touch command and by using a . infront of the file name.
For example lets say I type touch college, it would create a file with the name of college which wont be hidden and will be simply displayed by using the ls command.
But if I type touch .college, then it would create a hidden file which wont show up by simply using the ls command and some addition is necessary.
The addition is that -a has to be added in front of the ls command to display all the files including the hidden ones.
Now after learning this I went back to the module and it had instructed me to that a hidden file has been created inside of the directory ./
so, firstly I changed my directory by using the cd command to ./
Once I was in the cwd, I used the ls -a command to display all the files including the hidden ones.
This gave me a file with the name of .flag-11031127937, and then I used the cat command to read its contents.
This gave me the flag.

~~~
bash
ls
Desktop  delete_me  e
hacker@commands~hidden-files:~$ cd /.
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv         bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-11031127937  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cat .flag-11031127937
pwn.college{s8JZErCy2HboJJizefWUszoIFsM.dBTN4QDL5AjN0czW}
~~~

## An Epic Filesystem Quest
Oh God, this was such a long quest. But somehow I came on top at the end.
First of all, the module instructed me that I should change my directory to / by using the cd command.
Then inside it I have to read all the files which will lead me to some file which I have to read and the terminal keeps giving me some new directory every time which either I have to change my directory to by using cd or I have to directly read some text file inside it without changing my directory to it.
This kept on going for a while but finally after some time I got the flag.
All the files and commands can be found inside the code.
There was also a condition at the start that I couldnt change my directory or it would self destruct. But I had to change my directory to it, to get the name of the file which I had to read, the name of the file was BLUEPRINT-TRAPPED
But this self destructed the file and I had to restart my terminal, but after doing that I could now read the file without changing my directory and it worked.
I wont lie this module took alot of hit and trial such as going inside different directories and reading different files to find different clues but it definitely paid off at the end.

~~~
bash
 cd /
hacker@commands~an-epic-filesystem-quest:/$ cat BRIEF
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/Documentation/networking/device_drivers/dec

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/$ cat BLUEPRINT-TRAPPED
cat: BLUEPRINT-TRAPPED: No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ cat BLUEPRINT
cat: BLUEPRINT: No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/linux/linux-5.4/Documentation/networking/device_drivers/dec/BLUEPRINT-TRAPPED
Tubular find!
The next clue is in: /usr/local/lib/python3.8/dist-packages/jedi/third_party/django-stubs/django-stubs/contrib/admin/templatetags

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/local/lib/python3.8/dist-packages/jedi/third_party/django-stubs/django-stubs/contrib/admin/templatetags
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/jedi/third_party/django-stubs/django-stubs/contrib/admin/templatetags$ ls
ALERT  __init__.pyi  admin_list.pyi  admin_modify.pyi  admin_static.pyi  admin_urls.pyi  base.pyi  log.pyi
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/jedi/third_party/django-stubs/django-stubs/contrib/admin/templatetags$ ls -a
.  ..  ALERT  __init__.pyi  admin_list.pyi  admin_modify.pyi  admin_static.pyi  admin_urls.pyi  base.pyi  log.pyi
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/jedi/third_party/django-stubs/django-stubs/contrib/admin/templatetags$ cat ALERT
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/include/uapi/mtd

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/jedi/third_party/django-stubs/django-stubs/contrib/admin/templatetags$ cd /opt/linux/linux-5.4/include/uapi/mtd
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/uapi/mtd$ ls -a
.  ..  .MEMO  inftl-user.h  mtd-abi.h  mtd-user.h  nftl-user.h  ubi-user.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/uapi/mtd$ cat .MEMO
Tubular find!
The next clue is in: /usr/share/icons/ubuntu-mono-dark/status/22

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/uapi/mtd$ cd /usr/share/icons/ubuntu-mono-dark/status/22
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/ubuntu-mono-dark/status/22$ ls -a
.                                          indicator-keyboard-En-10.svg  indicator-keyboard-Kn-1.svg   indicator-keyboard-Th-1.svg
..                                         indicator-keyboard-En-11.svg  indicator-keyboard-Kn-2.svg   indicator-keyboard-Th-2.svg
CUE                                        indicator-keyboard-En-12.svg  indicator-keyboard-Kn.svg     indicator-keyboard-Th-3.svg
account-logged-in.svg                      indicator-keyboard-En-13.svg  indicator-keyboard-Ko-1.svg   indicator-keyboard-Th.svg
application-running.svg                    indicator-keyboard-En-14.svg  indicator-keyboard-Ko-2.svg   indicator-keyboard-Tk-1.svg
applications-chat-panel.svg                indicator-keyboard-En-15.svg  indicator-keyboard-Ko.svg     indicator-keyboard-Tk-2.svg
applications-email-panel.svg               indicator-keyboard-En-16.svg  indicator-keyboard-Ku-1.svg   indicator-keyboard-Tk.svg
audio-input-microphone-high-panel.svg      indicator-keyboard-En-17.svg  indicator-keyboard-Ku-10.svg  indicator-keyboard-Tn.svg
audio-input-microphone-low-zero-panel.svg  indicator-keyboard-En-18.svg  indicator-keyboard-Ku-11.svg  indicator-keyboard-Tr-1.svg
audio-output-none-panel.svg                indicator-keyboard-En-19.svg  indicator-keyboard-Ku-12.svg  indicator-keyboard-Tr-2.svg
audio-volume-high-panel.svg                indicator-keyboard-En-2.svg   indicator-keyboard-Ku-13.svg  indicator-keyboard-Tr-3.svg
audio-volume-low-panel.svg                 indicator-keyboard-En-20.svg  indicator-keyboard-Ku-14.svg  indicator-keyboard-Tr-4.svg
audio-volume-low-zero-panel.svg            indicator-keyboard-En-21.svg  indicator-keyboard-Ku-2.svg   indicator-keyboard-Tr-5.svg
audio-volume-medium-panel.svg              indicator-keyboard-En-22.svg  indicator-keyboard-Ku-3.svg   indicator-keyboard-Tr.svg
audio-volume-muted-blocking-panel.svg      indicator-keyboard-En-23.svg  indicator-keyboard-Ku-4.svg   indicator-keyboard-Uk-1.svg
audio-volume-muted-panel.svg               indicator-keyboard-En-24.svg  indicator-keyboard-Ku-5.svg   indicator-keyboard-Uk-2.svg
blueman-tray.svg                           indicator-keyboard-En-25.svg  indicator-keyboard-Ku-6.svg   indicator-keyboard-Uk-3.svg
bluetooth-active.svg                       indicator-keyboard-En-26.svg  indicator-keyboard-Ku-7.svg   indicator-keyboard-Uk-4.svg
bluetooth-disabled.svg                     indicator-keyboard-En-27.svg  indicator-keyboard-Ku-8.svg   indicator-keyboard-Uk-5.svg
bluetooth-paired.svg                       indicator-keyboard-En-28.svg  indicator-keyboard-Ku-9.svg   indicator-keyboard-Uk-6.svg
connect_creating.svg                       indicator-keyboard-En-29.svg  indicator-keyboard-Ku.svg     indicator-keyboard-Uk-7.svg
connect_established.svg                    indicator-keyboard-En-3.svg   indicator-keyboard-Lo-1.svg   indicator-keyboard-Uk-8.svg
connect_no.svg                             indicator-keyboard-En-30.svg  indicator-keyboard-Lo-2.svg   indicator-keyboard-Uk.svg
empathy-available.svg                      indicator-keyboard-En-31.svg  indicator-keyboard-Lo.svg     indicator-keyboard-Ur-1.svg
empathy-away.svg                           indicator-keyboard-En-32.svg  indicator-keyboard-Lt-1.svg   indicator-keyboard-Ur-2.svg
empathy-busy.svg                           indicator-keyboard-En-33.svg  indicator-keyboard-Lt-2.svg   indicator-keyboard-Ur-3.svg
empathy-extended-away.svg                  indicator-keyboard-En-34.svg  indicator-keyboard-Lt-3.svg   indicator-keyboard-Ur-4.svg
empathy-offline.svg                        indicator-keyboard-En-35.svg  indicator-keyboard-Lt-4.svg   indicator-keyboard-Ur-5.svg
gnome-netstatus-0-24.svg                   indicator-keyboard-En-4.svg   indicator-keyboard-Lt-5.svg   indicator-keyboard-Ur-6.svg
gnome-netstatus-25-49.svg                  indicator-keyboard-En-5.svg   indicator-keyboard-Lt-6.svg   indicator-keyboard-Ur.svg
gnome-netstatus-50-74.svg                  indicator-keyboard-En-6.svg   indicator-keyboard-Lt.svg     indicator-keyboard-Uz-1.svg
gnome-netstatus-75-100.svg                 indicator-keyboard-En-7.svg   indicator-keyboard-Lv-1.svg   indicator-keyboard-Uz-2.svg
gnome-netstatus-disconn.svg                indicator-keyboard-En-8.svg   indicator-keyboard-Lv-2.svg   indicator-keyboard-Uz-3.svg
gnome-netstatus-error.svg                  indicator-keyboard-En-9.svg   indicator-keyboard-Lv-3.svg   indicator-keyboard-Uz-4.svg
gnome-netstatus-idle.svg                   indicator-keyboard-En.svg     indicator-keyboard-Lv-4.svg   indicator-keyboard-Uz.svg
gnome-netstatus-rx.svg                     indicator-keyboard-Eo-1.svg   indicator-keyboard-Lv-5.svg   indicator-keyboard-Vi.svg
gnome-netstatus-tx.svg                     indicator-keyboard-Eo-2.svg   indicator-keyboard-Lv-6.svg   indicator-keyboard-Wo.svg
gnome-netstatus-txrx.svg                   indicator-keyboard-Eo.svg     indicator-keyboard-Lv-7.svg   indicator-keyboard-Xs.svg
gpm-keyboard-000.svg                       indicator-keyboard-Es-1.svg   indicator-keyboard-Lv.svg     indicator-keyboard-Yo.svg
gpm-keyboard-020.svg                       indicator-keyboard-Es-10.svg  indicator-keyboard-Md.svg     indicator-keyboard-Zh-1.svg
gpm-keyboard-040.svg                       indicator-keyboard-Es-11.svg  indicator-keyboard-Mi.svg     indicator-keyboard-Zh-2.svg
gpm-keyboard-060.svg                       indicator-keyboard-Es-12.svg  indicator-keyboard-Mk-1.svg   indicator-keyboard-Zh-3.svg
gpm-keyboard-080.svg                       indicator-keyboard-Es-2.svg   indicator-keyboard-Mk-2.svg   indicator-keyboard-Zh-4.svg
gpm-keyboard-100.svg                       indicator-keyboard-Es-3.svg   indicator-keyboard-Mk.svg     indicator-keyboard-Zh-5.svg
gpm-mouse-000.svg                          indicator-keyboard-Es-4.svg   indicator-keyboard-Ml-1.svg   indicator-keyboard-Zh-6.svg
gpm-mouse-020.svg                          indicator-keyboard-Es-5.svg   indicator-keyboard-Ml-2.svg   indicator-keyboard-Zh.svg
gpm-mouse-040.svg                          indicator-keyboard-Es-6.svg   indicator-keyboard-Ml-3.svg   indicator-messages-new.svg
gpm-mouse-060.svg                          indicator-keyboard-Es-7.svg   indicator-keyboard-Ml.svg     indicator-messages.svg
gpm-mouse-080.svg                          indicator-keyboard-Es-8.svg   indicator-keyboard-Mn.svg     krb-expiring-ticket.svg
gpm-mouse-100.svg                          indicator-keyboard-Es-9.svg   indicator-keyboard-Mr.svg     krb-no-valid-ticket.svg
gpm-phone-000.svg                          indicator-keyboard-Es.svg     indicator-keyboard-Mt-1.svg   krb-valid-ticket.svg
gpm-phone-020.svg                          indicator-keyboard-Et-1.svg   indicator-keyboard-Mt-2.svg   network-error.svg
gpm-phone-040.svg                          indicator-keyboard-Et-2.svg   indicator-keyboard-Mt.svg     network-idle.svg
gpm-phone-060.svg                          indicator-keyboard-Et-3.svg   indicator-keyboard-My.svg     network-offline.svg
gpm-phone-080.svg                          indicator-keyboard-Et-4.svg   indicator-keyboard-Ne.svg     network-receive.svg
gpm-phone-100.svg                          indicator-keyboard-Et.svg     indicator-keyboard-Nl-1.svg   network-transmit-receive.svg
gpm-primary-000-charging.svg               indicator-keyboard-Fa-1.svg   indicator-keyboard-Nl-2.svg   network-transmit.svg
gpm-primary-000.svg                        indicator-keyboard-Fa-2.svg   indicator-keyboard-Nl-3.svg   network-wired.svg
gpm-primary-020-charging.svg               indicator-keyboard-Fa-3.svg   indicator-keyboard-Nl-4.svg   new-messages-red.svg
gpm-primary-020.svg                        indicator-keyboard-Fa-4.svg   indicator-keyboard-Nl.svg     nm-adhoc.svg
gpm-primary-040-charging.svg               indicator-keyboard-Fa.svg     indicator-keyboard-No-1.svg   nm-device-wired-autoip.svg
gpm-primary-040.svg                        indicator-keyboard-Ff.svg     indicator-keyboard-No-2.svg   nm-device-wired-secure.svg
gpm-primary-060-charging.svg               indicator-keyboard-Fi-1.svg   indicator-keyboard-No-3.svg   nm-device-wired.svg
gpm-primary-060.svg                        indicator-keyboard-Fi-2.svg   indicator-keyboard-No-4.svg   nm-device-wwan.svg
gpm-primary-080-charging.svg               indicator-keyboard-Fi-3.svg   indicator-keyboard-No-5.svg   nm-mb-roam.svg
gpm-primary-080.svg                        indicator-keyboard-Fi-4.svg   indicator-keyboard-No-6.svg   nm-no-connection.svg
gpm-primary-100-charging.svg               indicator-keyboard-Fi-5.svg   indicator-keyboard-No-7.svg   nm-secure-lock.svg
gpm-primary-100.svg                        indicator-keyboard-Fi.svg     indicator-keyboard-No-8.svg   nm-signal-0.svg
gpm-primary-charged.svg                    indicator-keyboard-Fo-1.svg   indicator-keyboard-No.svg     nm-signal-00-secure.svg
gpm-ups-000-charging.svg                   indicator-keyboard-Fo-2.svg   indicator-keyboard-Or.svg     nm-signal-00.svg
gpm-ups-000.svg                            indicator-keyboard-Fo.svg     indicator-keyboard-Pa-1.svg   nm-signal-100-secure.svg
gpm-ups-020-charging.svg                   indicator-keyboard-Fr-1.svg   indicator-keyboard-Pa-2.svg   nm-signal-100.svg
gpm-ups-020.svg                            indicator-keyboard-Fr-10.svg  indicator-keyboard-Pa.svg     nm-signal-25-secure.svg
gpm-ups-040-charging.svg                   indicator-keyboard-Fr-11.svg  indicator-keyboard-Ph-1.svg   nm-signal-25.svg
gpm-ups-040.svg                            indicator-keyboard-Fr-12.svg  indicator-keyboard-Ph-10.svg  nm-signal-50-secure.svg
gpm-ups-060-charging.svg                   indicator-keyboard-Fr-13.svg  indicator-keyboard-Ph-2.svg   nm-signal-50.svg
gpm-ups-060.svg                            indicator-keyboard-Fr-14.svg  indicator-keyboard-Ph-3.svg   nm-signal-75-secure.svg
gpm-ups-080-charging.svg                   indicator-keyboard-Fr-15.svg  indicator-keyboard-Ph-4.svg   nm-signal-75.svg
gpm-ups-080.svg                            indicator-keyboard-Fr-16.svg  indicator-keyboard-Ph-5.svg   nm-tech-3g.svg
gpm-ups-100-charging.svg                   indicator-keyboard-Fr-17.svg  indicator-keyboard-Ph-6.svg   nm-tech-cdma-1x.svg
gpm-ups-100.svg                            indicator-keyboard-Fr-18.svg  indicator-keyboard-Ph-7.svg   nm-tech-edge.svg
gpm-ups-missing.svg                        indicator-keyboard-Fr-19.svg  indicator-keyboard-Ph-8.svg   nm-tech-evdo.svg
gsm-3g-full-secure.svg                     indicator-keyboard-Fr-2.svg   indicator-keyboard-Ph-9.svg   nm-tech-gprs.svg
gsm-3g-full.svg                            indicator-keyboard-Fr-20.svg  indicator-keyboard-Ph.svg     nm-tech-hspa.svg
gsm-3g-high-secure.svg                     indicator-keyboard-Fr-21.svg  indicator-keyboard-Pl-1.svg   nm-tech-umts.svg
gsm-3g-high.svg                            indicator-keyboard-Fr-22.svg  indicator-keyboard-Pl-2.svg   nm-vpn-active-lock.svg
gsm-3g-low-secure.svg                      indicator-keyboard-Fr-23.svg  indicator-keyboard-Pl-3.svg   nm-vpn-lock.svg
gsm-3g-low.svg                             indicator-keyboard-Fr-24.svg  indicator-keyboard-Pl-4.svg   nm-vpn-standalone-lock.svg
gsm-3g-medium-secure.svg                   indicator-keyboard-Fr-25.svg  indicator-keyboard-Pl-5.svg   nm-wwan-tower.svg
gsm-3g-medium.svg                          indicator-keyboard-Fr-26.svg  indicator-keyboard-Pl-6.svg   stock_disconnect.svg
gsm-3g-none-secure.svg                     indicator-keyboard-Fr-27.svg  indicator-keyboard-Pl-7.svg   system-devices-panel-alert.svg
gsm-3g-none.svg                            indicator-keyboard-Fr-28.svg  indicator-keyboard-Pl-8.svg   system-devices-panel-information.svg
gtk-dialog-authentication-panel.svg        indicator-keyboard-Fr-29.svg  indicator-keyboard-Pl-9.svg   system-devices-panel.svg
ibus-keyboard.svg                          indicator-keyboard-Fr-3.svg   indicator-keyboard-Pl.svg     tray-away.svg
im-message-new.svg                         indicator-keyboard-Fr-30.svg  indicator-keyboard-Ps-1.svg   tray-busy.svg
indicator-appmenu-menu-panel.svg           indicator-keyboard-Fr-31.svg  indicator-keyboard-Ps-2.svg   tray-extended-away.svg
indicator-keyboard-Ak.svg                  indicator-keyboard-Fr-4.svg   indicator-keyboard-Ps.svg     tray-message.svg
indicator-keyboard-Am.svg                  indicator-keyboard-Fr-5.svg   indicator-keyboard-Pt-1.svg   tray-new-im.svg
indicator-keyboard-Ar-1.svg                indicator-keyboard-Fr-6.svg   indicator-keyboard-Pt-10.svg  tray-offline.svg
indicator-keyboard-Ar-10.svg               indicator-keyboard-Fr-7.svg   indicator-keyboard-Pt-11.svg  tray-online.svg
indicator-keyboard-Ar-11.svg               indicator-keyboard-Fr-8.svg   indicator-keyboard-Pt-12.svg  ubuntuone-client-error.svg
indicator-keyboard-Ar-2.svg                indicator-keyboard-Fr-9.svg   indicator-keyboard-Pt-13.svg  ubuntuone-client-idle.svg
indicator-keyboard-Ar-3.svg                indicator-keyboard-Fr.svg     indicator-keyboard-Pt-14.svg  ubuntuone-client-offline.svg
indicator-keyboard-Ar-4.svg                indicator-keyboard-Ga-1.svg   indicator-keyboard-Pt-15.svg  ubuntuone-client-paused.svg
indicator-keyboard-Ar-5.svg                indicator-keyboard-Ga-2.svg   indicator-keyboard-Pt-2.svg   ubuntuone-client-updating.svg
indicator-keyboard-Ar-6.svg                indicator-keyboard-Ga.svg     indicator-keyboard-Pt-3.svg   unity-ac-adapter-symbolic.svg
indicator-keyboard-Ar-7.svg                indicator-keyboard-Gr-1.svg   indicator-keyboard-Pt-4.svg   unity-battery-000-charging.svg
indicator-keyboard-Ar-8.svg                indicator-keyboard-Gr-2.svg   indicator-keyboard-Pt-5.svg   unity-battery-000.svg
indicator-keyboard-Ar-9.svg                indicator-keyboard-Gr-3.svg   indicator-keyboard-Pt-6.svg   unity-battery-020-charging.svg
indicator-keyboard-Ar.svg                  indicator-keyboard-Gr-4.svg   indicator-keyboard-Pt-7.svg   unity-battery-020.svg
indicator-keyboard-Av.svg                  indicator-keyboard-Gr-5.svg   indicator-keyboard-Pt-8.svg   unity-battery-040-charging.svg
indicator-keyboard-Az-1.svg                indicator-keyboard-Gr.svg     indicator-keyboard-Pt-9.svg   unity-battery-040.svg
indicator-keyboard-Az-2.svg                indicator-keyboard-Gu.svg     indicator-keyboard-Pt.svg     unity-battery-060-charging.svg
indicator-keyboard-Az.svg                  indicator-keyboard-Ha-1.svg   indicator-keyboard-Ro-1.svg   unity-battery-060.svg
indicator-keyboard-Be-1.svg                indicator-keyboard-Ha-2.svg   indicator-keyboard-Ro-2.svg   unity-battery-080-charging.svg
indicator-keyboard-Be-10.svg               indicator-keyboard-Ha.svg     indicator-keyboard-Ro-3.svg   unity-battery-080.svg
indicator-keyboard-Be-11.svg               indicator-keyboard-He-1.svg   indicator-keyboard-Ro-4.svg   unity-battery-100-charging.svg
indicator-keyboard-Be-12.svg               indicator-keyboard-He-2.svg   indicator-keyboard-Ro-5.svg   unity-battery-100.svg
indicator-keyboard-Be-13.svg               indicator-keyboard-He-3.svg   indicator-keyboard-Ro.svg     unity-battery-caution-charging-symbolic.svg
indicator-keyboard-Be-14.svg               indicator-keyboard-He-4.svg   indicator-keyboard-Ru-1.svg   unity-battery-caution-symbolic.svg
indicator-keyboard-Be-2.svg                indicator-keyboard-He.svg     indicator-keyboard-Ru-10.svg  unity-battery-caution.svg
indicator-keyboard-Be-3.svg                indicator-keyboard-Hi-1.svg   indicator-keyboard-Ru-11.svg  unity-battery-charged.svg
indicator-keyboard-Be-4.svg                indicator-keyboard-Hi-2.svg   indicator-keyboard-Ru-12.svg  unity-battery-empty-charging-symbolic.svg
indicator-keyboard-Be-5.svg                indicator-keyboard-Hi-3.svg   indicator-keyboard-Ru-13.svg  unity-battery-empty-symbolic.svg
indicator-keyboard-Be-6.svg                indicator-keyboard-Hi.svg     indicator-keyboard-Ru-14.svg  unity-battery-full-charged-symbolic.svg
indicator-keyboard-Be-7.svg                indicator-keyboard-Hr-1.svg   indicator-keyboard-Ru-15.svg  unity-battery-full-charging-symbolic.svg
indicator-keyboard-Be-8.svg                indicator-keyboard-Hr-2.svg   indicator-keyboard-Ru-16.svg  unity-battery-full-symbolic.svg
indicator-keyboard-Be-9.svg                indicator-keyboard-Hr-3.svg   indicator-keyboard-Ru-17.svg  unity-battery-good-charging-symbolic.svg
indicator-keyboard-Be.svg                  indicator-keyboard-Hr-4.svg   indicator-keyboard-Ru-18.svg  unity-battery-good-symbolic.svg
indicator-keyboard-Bg-1.svg                indicator-keyboard-Hr-5.svg   indicator-keyboard-Ru-19.svg  unity-battery-low-charging-symbolic.svg
indicator-keyboard-Bg-2.svg                indicator-keyboard-Hr.svg     indicator-keyboard-Ru-2.svg   unity-battery-low-symbolic.svg
indicator-keyboard-Bg-3.svg                indicator-keyboard-Hu-1.svg   indicator-keyboard-Ru-20.svg  unity-battery-low.svg
indicator-keyboard-Bg.svg                  indicator-keyboard-Hu-10.svg  indicator-keyboard-Ru-21.svg  unity-battery-missing-symbolic.svg
indicator-keyboard-Bm.svg                  indicator-keyboard-Hu-11.svg  indicator-keyboard-Ru-22.svg  unity-battery_charged.svg
indicator-keyboard-Bn-1.svg                indicator-keyboard-Hu-12.svg  indicator-keyboard-Ru-23.svg  unity-battery_empty.svg
indicator-keyboard-Bn-2.svg                indicator-keyboard-Hu-13.svg  indicator-keyboard-Ru-24.svg  unity-battery_full.svg
indicator-keyboard-Bn-3.svg                indicator-keyboard-Hu-14.svg  indicator-keyboard-Ru-25.svg  unity-battery_plugged.svg
indicator-keyboard-Bn-4.svg                indicator-keyboard-Hu-15.svg  indicator-keyboard-Ru-26.svg  unity-gpm-battery-000-charging.svg
indicator-keyboard-Bn.svg                  indicator-keyboard-Hu-16.svg  indicator-keyboard-Ru-27.svg  unity-gpm-battery-000.svg
indicator-keyboard-Br-1.svg                indicator-keyboard-Hu-17.svg  indicator-keyboard-Ru-3.svg   unity-gpm-battery-020-charging.svg
indicator-keyboard-Br-2.svg                indicator-keyboard-Hu-18.svg  indicator-keyboard-Ru-4.svg   unity-gpm-battery-020.svg
indicator-keyboard-Br-3.svg                indicator-keyboard-Hu-19.svg  indicator-keyboard-Ru-5.svg   unity-gpm-battery-040-charging.svg
indicator-keyboard-Br.svg                  indicator-keyboard-Hu-2.svg   indicator-keyboard-Ru-6.svg   unity-gpm-battery-040.svg
indicator-keyboard-Bs-1.svg                indicator-keyboard-Hu-20.svg  indicator-keyboard-Ru-7.svg   unity-gpm-battery-060-charging.svg
indicator-keyboard-Bs-2.svg                indicator-keyboard-Hu-3.svg   indicator-keyboard-Ru-8.svg   unity-gpm-battery-060.svg
indicator-keyboard-Bs-3.svg                indicator-keyboard-Hu-4.svg   indicator-keyboard-Ru-9.svg   unity-gpm-battery-080-charging.svg
indicator-keyboard-Bs-4.svg                indicator-keyboard-Hu-5.svg   indicator-keyboard-Ru.svg     unity-gpm-battery-080.svg
indicator-keyboard-Bs-5.svg                indicator-keyboard-Hu-6.svg   indicator-keyboard-Sa.svg     unity-gpm-battery-100-charging.svg
indicator-keyboard-Bs.svg                  indicator-keyboard-Hu-7.svg   indicator-keyboard-Sd.svg     unity-gpm-battery-100.svg
indicator-keyboard-By-1.svg                indicator-keyboard-Hu-8.svg   indicator-keyboard-Si-1.svg   unity-gpm-battery-charged.svg
indicator-keyboard-By-2.svg                indicator-keyboard-Hu-9.svg   indicator-keyboard-Si-2.svg   unity-gpm-battery-empty.svg
indicator-keyboard-By-3.svg                indicator-keyboard-Hu.svg     indicator-keyboard-Si.svg     unity-gpm-battery-missing.svg
indicator-keyboard-By.svg                  indicator-keyboard-Hy-1.svg   indicator-keyboard-Sk-1.svg   user-available-panel.svg
indicator-keyboard-Ch.svg                  indicator-keyboard-Hy-2.svg   indicator-keyboard-Sk-2.svg   user-away-panel.svg
indicator-keyboard-Cm-1.svg                indicator-keyboard-Hy-3.svg   indicator-keyboard-Sk-3.svg   user-busy-panel.svg
indicator-keyboard-Cm-2.svg                indicator-keyboard-Hy-4.svg   indicator-keyboard-Sk-4.svg   user-idle-panel.svg
indicator-keyboard-Cm-3.svg                indicator-keyboard-Hy-5.svg   indicator-keyboard-Sk.svg     user-indeterminate-panel.svg
indicator-keyboard-Cm-4.svg                indicator-keyboard-Hy-6.svg   indicator-keyboard-Sl-1.svg   user-invisible-panel.svg
indicator-keyboard-Cm-5.svg                indicator-keyboard-Hy.svg     indicator-keyboard-Sl-2.svg   user-offline-panel.svg
indicator-keyboard-Cm.svg                  indicator-keyboard-Ie-1.svg   indicator-keyboard-Sl-3.svg   xfce4-mixer-muted.svg
indicator-keyboard-Cr-1.svg                indicator-keyboard-Ie-2.svg   indicator-keyboard-Sl.svg     xfce4-mixer-no-record.svg
indicator-keyboard-Cr-2.svg                indicator-keyboard-Ie-3.svg   indicator-keyboard-Sq.svg     xfce4-mixer-record.svg
indicator-keyboard-Cr-3.svg                indicator-keyboard-Ie-4.svg   indicator-keyboard-Sr-1.svg   xfce4-mixer-volume-muted.svg
indicator-keyboard-Cr.svg                  indicator-keyboard-Ie-5.svg   indicator-keyboard-Sr-10.svg  xfpm-ac-adapter.svg
indicator-keyboard-Cs-1.svg                indicator-keyboard-Ie.svg     indicator-keyboard-Sr-11.svg  xfpm-keyboard-000.svg
indicator-keyboard-Cs-2.svg                indicator-keyboard-Ig.svg     indicator-keyboard-Sr-12.svg  xfpm-keyboard-030.svg
indicator-keyboard-Cs-3.svg                indicator-keyboard-Ik.svg     indicator-keyboard-Sr-13.svg  xfpm-keyboard-060.svg
indicator-keyboard-Cs-4.svg                indicator-keyboard-In-1.svg   indicator-keyboard-Sr-14.svg  xfpm-keyboard-100.svg
indicator-keyboard-Cs-5.svg                indicator-keyboard-In-2.svg   indicator-keyboard-Sr-15.svg  xfpm-mouse-000.svg
indicator-keyboard-Cs-6.svg                indicator-keyboard-In-3.svg   indicator-keyboard-Sr-16.svg  xfpm-mouse-030.svg
indicator-keyboard-Cs.svg                  indicator-keyboard-In-4.svg   indicator-keyboard-Sr-17.svg  xfpm-mouse-060.svg
indicator-keyboard-Da-1.svg                indicator-keyboard-In-5.svg   indicator-keyboard-Sr-2.svg   xfpm-mouse-100.svg
indicator-keyboard-Da-2.svg                indicator-keyboard-In.svg     indicator-keyboard-Sr-3.svg   xfpm-phone-000.svg
indicator-keyboard-Da-3.svg                indicator-keyboard-Is-1.svg   indicator-keyboard-Sr-4.svg   xfpm-phone-040.svg
indicator-keyboard-Da-4.svg                indicator-keyboard-Is-2.svg   indicator-keyboard-Sr-5.svg   xfpm-phone-060.svg
indicator-keyboard-Da-5.svg                indicator-keyboard-Is-3.svg   indicator-keyboard-Sr-6.svg   xfpm-phone-100.svg
indicator-keyboard-Da.svg                  indicator-keyboard-Is-4.svg   indicator-keyboard-Sr-7.svg   xfpm-primary-000-charging.svg
indicator-keyboard-De-1.svg                indicator-keyboard-Is-5.svg   indicator-keyboard-Sr-8.svg   xfpm-primary-000.svg
indicator-keyboard-De-10.svg               indicator-keyboard-Is.svg     indicator-keyboard-Sr-9.svg   xfpm-primary-020-charging.svg
indicator-keyboard-De-11.svg               indicator-keyboard-It-1.svg   indicator-keyboard-Sr.svg     xfpm-primary-020.svg
indicator-keyboard-De-12.svg               indicator-keyboard-It-2.svg   indicator-keyboard-Sv-1.svg   xfpm-primary-040-charging.svg
indicator-keyboard-De-13.svg               indicator-keyboard-It-3.svg   indicator-keyboard-Sv-2.svg   xfpm-primary-040.svg
indicator-keyboard-De-14.svg               indicator-keyboard-It-4.svg   indicator-keyboard-Sv-3.svg   xfpm-primary-060-charging.svg
indicator-keyboard-De-15.svg               indicator-keyboard-It-5.svg   indicator-keyboard-Sv-4.svg   xfpm-primary-060.svg
indicator-keyboard-De-16.svg               indicator-keyboard-It-6.svg   indicator-keyboard-Sv-5.svg   xfpm-primary-080-charging.svg
indicator-keyboard-De-17.svg               indicator-keyboard-It.svg     indicator-keyboard-Sv-6.svg   xfpm-primary-080.svg
indicator-keyboard-De-18.svg               indicator-keyboard-Ja-1.svg   indicator-keyboard-Sv-7.svg   xfpm-primary-100-charging.svg
indicator-keyboard-De-19.svg               indicator-keyboard-Ja-2.svg   indicator-keyboard-Sv.svg     xfpm-primary-100.svg
indicator-keyboard-De-2.svg                indicator-keyboard-Ja-3.svg   indicator-keyboard-Sw-1.svg   xfpm-primary-charged.svg
indicator-keyboard-De-20.svg               indicator-keyboard-Ja-4.svg   indicator-keyboard-Sw-2.svg   xfpm-primary-missing.svg
indicator-keyboard-De-21.svg               indicator-keyboard-Ja-5.svg   indicator-keyboard-Sw.svg     xfpm-ups-000-charging.svg
indicator-keyboard-De-22.svg               indicator-keyboard-Ja-6.svg   indicator-keyboard-Sy-1.svg   xfpm-ups-000.svg
indicator-keyboard-De-23.svg               indicator-keyboard-Ja-7.svg   indicator-keyboard-Sy-2.svg   xfpm-ups-020-charging.svg
indicator-keyboard-De-24.svg               indicator-keyboard-Ja.svg     indicator-keyboard-Sy.svg     xfpm-ups-020.svg
indicator-keyboard-De-25.svg               indicator-keyboard-Ka-1.svg   indicator-keyboard-Ta-1.svg   xfpm-ups-040-charging.svg
indicator-keyboard-De-3.svg                indicator-keyboard-Ka-2.svg   indicator-keyboard-Ta-2.svg   xfpm-ups-040.svg
indicator-keyboard-De-4.svg                indicator-keyboard-Ka-3.svg   indicator-keyboard-Ta-3.svg   xfpm-ups-060-charging.svg
indicator-keyboard-De-5.svg                indicator-keyboard-Ka-4.svg   indicator-keyboard-Ta-4.svg   xfpm-ups-060.svg
indicator-keyboard-De-6.svg                indicator-keyboard-Ka.svg     indicator-keyboard-Ta-5.svg   xfpm-ups-080-charging.svg
indicator-keyboard-De-7.svg                indicator-keyboard-Ki-1.svg   indicator-keyboard-Ta-6.svg   xfpm-ups-080.svg
indicator-keyboard-De-8.svg                indicator-keyboard-Ki-2.svg   indicator-keyboard-Ta.svg     xfpm-ups-100-charging.svg
indicator-keyboard-De-9.svg                indicator-keyboard-Ki-3.svg   indicator-keyboard-Te-1.svg   xfpm-ups-100.svg
indicator-keyboard-De.svg                  indicator-keyboard-Ki.svg     indicator-keyboard-Te-2.svg   xfpm-ups-charged.svg
indicator-keyboard-Dv.svg                  indicator-keyboard-Kk-1.svg   indicator-keyboard-Te.svg     xfpm-ups-missing.svg
indicator-keyboard-Dz.svg                  indicator-keyboard-Kk-2.svg   indicator-keyboard-Tg-1.svg
indicator-keyboard-Ee.svg                  indicator-keyboard-Kk.svg     indicator-keyboard-Tg-2.svg
indicator-keyboard-En-1.svg                indicator-keyboard-Km.svg     indicator-keyboard-Tg.svg
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/ubuntu-mono-dark/status/22$ cat LUE
cat: LUE: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/ubuntu-mono-dark/status/22$ cat CUE
Tubular find!
The next clue is in: /usr/share/racket/pkgs/games/cards/locolor
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/ubuntu-mono-dark/status/22$ cd /usr/share/racket/pkgs/games/cards/locolor
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/games/cards/locolor$ ls -a
.             card-0-3.png   card-10-1.png  card-11-3.png  card-2-1.png  card-3-3.png  card-5-1.png  card-6-3.png  card-8-1.png  card-9-3.png
..            card-1-0.png   card-10-2.png  card-12-0.png  card-2-2.png  card-4-0.png  card-5-2.png  card-7-0.png  card-8-2.png  card-back.png
CLUE          card-1-1.png   card-10-3.png  card-12-1.png  card-2-3.png  card-4-1.png  card-5-3.png  card-7-1.png  card-8-3.png
card-0-0.png  card-1-2.png   card-11-0.png  card-12-2.png  card-3-0.png  card-4-2.png  card-6-0.png  card-7-2.png  card-9-0.png
card-0-1.png  card-1-3.png   card-11-1.png  card-12-3.png  card-3-1.png  card-4-3.png  card-6-1.png  card-7-3.png  card-9-1.png
card-0-2.png  card-10-0.png  card-11-2.png  card-2-0.png   card-3-2.png  card-5-0.png  card-6-2.png  card-8-0.png  card-9-2.png
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/games/cards/locolor$ cat CLUE
Great sleuthing!
The next clue is in: /usr/local/lib/python3.8/dist-packages/jupyterlab_pygments-0.3.0.dist-info/licenses

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/games/cards/locolor$ cd /usr/local/lib/python3.8/dist-packages/jupyterlab_pygments-0.3.0.dist-info/licenses
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/jupyterlab_pygments-0.3.0.dist-info/licenses$ ls -a
.  ..  GIST  LICENSE
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/jupyterlab_pygments-0.3.0.dist-info/licenses$ cat GIST
Great sleuthing!
The next clue is in: /usr/share/help/el

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/jupyterlab_pygments-0.3.0.dist-info/licenses$ cd /usr/share/help/el
hacker@commands~an-epic-filesystem-quest:/usr/share/help/el$ ls -a
.  ..  .TEASER  gedit
hacker@commands~an-epic-filesystem-quest:/usr/share/help/el$ cat TEASER
cat: TEASER: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/share/help/el$ cat .TEASTER
cat: .TEASTER: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/share/help/el$ cat .TEASER
Tubular find!
The next clue is in: /usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/third_party/2/six/moves

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/share/help/el$ cd /usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/third_party/2/six/moves
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/third_party/2/six/moves$ ls -a
.                   SimpleHTTPServer.pyi  collections_abc.pyi          email_mime_text.pyi  http_cookies.pyi  urllib_error.pyi        xmlrpc_client.pyi
..                  __init__.pyi          configparser.pyi             html_entities.pyi    queue.pyi         urllib_parse.pyi
.TRACE              _dummy_thread.pyi     email_mime_base.pyi          html_parser.pyi      reprlib.pyi       urllib_request.pyi
BaseHTTPServer.pyi  _thread.pyi           email_mime_multipart.pyi     http_client.pyi      socketserver.pyi  urllib_response.pyi
CGIHTTPServer.pyi   cPickle.pyi           email_mime_nonmultipart.pyi  http_cookiejar.pyi   urllib            urllib_robotparser.pyi
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/third_party/2/six/moves$ cat .TRACE
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{4fIT53MyflpCpP6nZojUAai3jr2.dljM4QDL5AjN0czW}
~~~

## making directories
This module taught me on how to make a directory using the mkdir command and then successively files can be put inside it using the touch command which I learnt earlier.
The module instructed me that I had to create a /tmp/pwn directory using the mkdir command.
Then I had to change my directory to /tmp/pwn which I just created using the cd command.
Then once my directory was changed I had to create a file inside it using the touch command.
I created the file college in it.
Then I ran /challenge/run to make sure that the directory and the file were created, and the flag was obtained.

~~~
bash
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{AIFNzTluQea7xW_WSfx-d5eS0xs.dFzM4QDL5AjN0czW}
hacker@commands~making-directories:/tmp/pwn$
~~~


## finding files
In this module I learnt about a new command find which can search and find a specific file inside of a directory or in the home directory.
Firstly I just put changed my directory to / by using cd and then typed in find, which was the worst mistake of my life, as it had like millions of files and the command terminal kept running and showed me new files like how a language does when you run an infinite loop.
I had to exit the terminal and start again due to this problem which I had created.
Now again in the terminal, I knew that I could not search in the whole directory so I tried using find flag but it gave me an error that flag does not exist.
Then I read the instructions of the module again as I had to use some specific command to find flag but after trying some trial and error I couldnt figure it out.
Then I reffered to the following video for help ------> https://www.youtube.com/watch?v=oPdFGUrq-XQ&ab_channel=GeeksforGeeks
Which made me realize that in the changed directory / I had to run this command to find the flag (find ./ -type f -name flag)
This gave me several flag files which had their permission/access denied, but there was only one which could be accessed.
I used the cat command on that file and it gave me the flag.
~~~
bash
hacker@commands~finding-files:~$ cd /
hacker@commands~finding-files:/$ find ./ -type f -name flag
find: ‘./root’: Permission denied
find: ‘./proc/1/task/1/fd’: Permission denied
find: ‘./proc/1/task/1/fdinfo’: Permission denied
find: ‘./proc/1/task/1/ns’: Permission denied
find: ‘./proc/1/fd’: Permission denied
find: ‘./proc/1/map_files’: Permission denied
find: ‘./proc/1/fdinfo’: Permission denied
find: ‘./proc/1/ns’: Permission denied
find: ‘./proc/7/task/7/fd’: Permission denied
find: ‘./proc/7/task/7/fdinfo’: Permission denied
find: ‘./proc/7/task/7/ns’: Permission denied
find: ‘./proc/7/fd’: Permission denied
find: ‘./proc/7/map_files’: Permission denied
find: ‘./proc/7/fdinfo’: Permission denied
find: ‘./proc/7/ns’: Permission denied
find: ‘./var/log/private’: Permission denied
find: ‘./var/log/apache2’: Permission denied
find: ‘./var/log/mysql’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/php/sessions’: Permission denied
find: ‘./var/lib/mysql-files’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/mysql-keyring’: Permission denied
find: ‘./var/lib/mysql’: Permission denied
find: ‘./tmp/tmp.XvrUsDZh8M’: Permission denied
find: ‘./run/mysqld’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
./usr/share/doc/netcat-openbsd/examples/flag
hacker@commands~finding-files:/$ cat ./usr/share/doc/netcat-openbsd/examples/flag
~~~
This is how I obtained the flag for this module.

## linking files
this was a particularly weird module as it made me think quite a lot, but a good one as well.
this module basically taught me about hard and soft links aka symbolic links.
also reffered to the following link to understand more about both the type of links -----> https://www.geeksforgeeks.org/difference-between-hard-link-and-soft-link/
the basic difference between the two is that hard link acts as a copy of some file and has access to that data.
whilst soft link acts as a reference to the orignal data file and doesnt access it, only refers to it like that similar to that of a pointer.
proceeding into the module it educates me about the -s argument which can be used with the ln command to create symbolic links to refer to the original data file.
the ln command is basically used to establish a link between two files.
then the module gave me the sample syntax or method to use the ln -s command to establish a link.
Also learnt about the file command, which basically returns the file type of a given file.
Now proceeding to the question, the module instructs me that the command /challenge/flag would read out /home/hacker/not-the-flag and not the flag, hence I have to change the symlink from /home/hacker/not-the-flag to /flag to read the contents of /flag to obtain the flag.
Now firstly by reading the module I got to know about the syntax which was used to refer to some files basically using symlinks, so I did that inside the terminal and used the command ln -s /flag /home/hacker/not-the-flag after changing my directory to / by using the cd command.
But to my surprise, the ln -s command gave me an error link '/flag': File exists and I got confused and didnt know how to proceed further as it would just not change the symlink from /home/hacker/not-the-flag to /flag.
After some discussion with a friend(who is not in the task phase but has information regarding linux), I realized that I had to use the rm command to remove the file permanently so that it wouldnt give me the error that the file already exists. after using the command  rm /home/hacker/not-the-flag, the file was removed and then I could run the above command error free and then finally invoked the catflag program and it gave me the flag.
~~~
bash
hacker@commands~linking-files:~$ cd /
hacker@commands~linking-files:/$ ln -s /flag /home/hacker/not-the-flag
ln: failed to create symbolic link '/home/hacker/not-the-flag': File exists
hacker@commands~linking-files:/$ rm /home/hacker/not-the-flag
hacker@commands~linking-files:/$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:/$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{YomfbUKlgMZg1ErJE6eWITJyIrc.dlTM1UDL5AjN0czW}
~~~



