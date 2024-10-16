# Level 6
In this level I was given some file properties which I had to exploit to find the file for the password.
the 2 properties which I used were size 33 and the user was bandit7.
used the find command with the above properties and got the password.
~~~
bash
bandit6@bandit:/$ find -user bandit7 -size 33c
find: ‘./drifter/drifter14_src/axTLS’: Permission denied
find: ‘./root’: Permission denied
find: ‘./snap’: Permission denied
find: ‘./tmp’: Permission denied
find: ‘./proc/tty/driver’: Permission denied
find: ‘./proc/1066490/task/1066490/fd/6’: No such file or directory
find: ‘./proc/1066490/task/1066490/fdinfo/6’: No such file or directory
find: ‘./proc/1066490/fd/5’: No such file or directory
find: ‘./proc/1066490/fdinfo/5’: No such file or directory
find: ‘./home/bandit31-git’: Permission denied
find: ‘./home/ubuntu’: Permission denied
find: ‘./home/bandit5/inhere’: Permission denied
find: ‘./home/bandit30-git’: Permission denied
find: ‘./home/drifter8/chroot’: Permission denied
find: ‘./home/drifter6/data’: Permission denied
find: ‘./home/bandit29-git’: Permission denied
find: ‘./home/bandit28-git’: Permission denied
find: ‘./home/bandit27-git’: Permission denied
find: ‘./lost+found’: Permission denied
find: ‘./etc/polkit-1/rules.d’: Permission denied
find: ‘./etc/multipath’: Permission denied
find: ‘./etc/stunnel’: Permission denied
find: ‘./etc/xinetd.d’: Permission denied
find: ‘./etc/credstore.encrypted’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
./etc/bandit_pass/bandit7
find: ‘./etc/sudoers.d’: Permission denied
find: ‘./etc/credstore’: Permission denied
find: ‘./dev/shm’: Permission denied
find: ‘./dev/mqueue’: Permission denied
find: ‘./var/log/amazon’: Permission denied
find: ‘./var/log/unattended-upgrades’: Permission denied
find: ‘./var/log/chrony’: Permission denied
find: ‘./var/log/private’: Permission denied
find: ‘./var/tmp’: Permission denied
find: ‘./var/spool/cron/crontabs’: Permission denied
find: ‘./var/spool/bandit24’: Permission denied
find: ‘./var/spool/rsyslog’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/pollinate’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/cache/apparmor/2425d902.0’: Permission denied
find: ‘./var/cache/apparmor/baad73a1.0’: Permission denied
find: ‘./var/lib/polkit-1’: Permission denied
find: ‘./var/lib/amazon’: Permission denied
./var/lib/dpkg/info/bandit7.password
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/chrony’: Permission denied
find: ‘./var/lib/snapd/void’: Permission denied
find: ‘./var/lib/snapd/cookie’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/ubuntu-advantage/apt-esm/var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/update-notifier/package-data-downloads/partial’: Permission denied
find: ‘./var/lib/udisks2’: Permission denied
find: ‘./var/crash’: Permission denied
find: ‘./boot/efi’: Permission denied
find: ‘./boot/lost+found’: Permission denied
find: ‘./sys/kernel/tracing’: Permission denied
find: ‘./sys/kernel/debug’: Permission denied
find: ‘./sys/fs/pstore’: Permission denied
find: ‘./sys/fs/bpf’: Permission denied
find: ‘./run/lock/lvm’: Permission denied
find: ‘./run/systemd/inaccessible/dir’: Permission denied
find: ‘./run/systemd/propagate/systemd-udevd.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-resolved.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-networkd.service’: Permission denied
find: ‘./run/systemd/propagate/irqbalance.service’: Permission denied
find: ‘./run/systemd/propagate/systemd-logind.service’: Permission denied
find: ‘./run/systemd/propagate/chrony.service’: Permission denied
find: ‘./run/systemd/propagate/polkit.service’: Permission denied
find: ‘./run/systemd/propagate/ModemManager.service’: Permission denied
find: ‘./run/systemd/propagate/fwupd.service’: Permission denied
find: ‘./run/systemd/propagate/bolt.service’: Permission denied
find: ‘./run/lvm’: Permission denied
find: ‘./run/log/journal/ec2dd69f90c4a6285216f71caca9bbca’: Permission denied
find: ‘./run/cryptsetup’: Permission denied
find: ‘./run/multipath’: Permission denied
find: ‘./run/screen/S-bandit20’: Permission denied
find: ‘./run/screen/S-bandit27’: Permission denied
find: ‘./run/screen/S-bandit28’: Permission denied
find: ‘./run/screen/S-bandit24’: Permission denied
find: ‘./run/screen/S-bandit17’: Permission denied
find: ‘./run/screen/S-bandit12’: Permission denied
find: ‘./run/screen/S-bandit29’: Permission denied
find: ‘./run/screen/S-bandit23’: Permission denied
find: ‘./run/screen/S-bandit1’: Permission denied
find: ‘./run/screen/S-bandit31’: Permission denied
find: ‘./run/screen/S-bandit21’: Permission denied
find: ‘./run/screen/S-bandit22’: Permission denied
find: ‘./run/screen/S-bandit19’: Permission denied
find: ‘./run/screen/S-bandit30’: Permission denied
find: ‘./run/screen/S-bandit33’: Permission denied
find: ‘./run/screen/S-bandit25’: Permission denied
find: ‘./run/screen/S-bandit16’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./run/user/11000’: Permission denied
find: ‘./run/user/11012’: Permission denied
find: ‘./run/user/11001’: Permission denied
find: ‘./run/user/11013’: Permission denied
find: ‘./run/user/11023’: Permission denied
find: ‘./run/user/11016’: Permission denied
find: ‘./run/user/11028’: Permission denied
find: ‘./run/user/11024’: Permission denied
find: ‘./run/user/11027’: Permission denied
find: ‘./run/user/11005’: Permission denied
find: ‘./run/user/11015’: Permission denied
find: ‘./run/user/11003’: Permission denied
find: ‘./run/user/11020’: Permission denied
find: ‘./run/user/11004’: Permission denied
find: ‘./run/user/11032’: Permission denied
find: ‘./run/user/11025’: Permission denied
find: ‘./run/user/11002’: Permission denied
find: ‘./run/user/11026’: Permission denied
find: ‘./run/user/20000’: Permission denied
find: ‘./run/user/11006/systemd/inaccessible/dir’: Permission denied
find: ‘./run/user/11008’: Permission denied
find: ‘./run/user/11014’: Permission denied
find: ‘./run/user/11009’: Permission denied
find: ‘./run/user/11011’: Permission denied
find: ‘./run/user/11007’: Permission denied
find: ‘./run/user/11019’: Permission denied
find: ‘./run/user/11029’: Permission denied
find: ‘./run/user/11010’: Permission denied
find: ‘./run/user/11017’: Permission denied
find: ‘./run/user/11018’: Permission denied
find: ‘./run/user/11021’: Permission denied
find: ‘./run/user/11031’: Permission denied
find: ‘./run/user/11022’: Permission denied
find: ‘./run/user/11033’: Permission denied
find: ‘./run/user/11531’: Permission denied
find: ‘./run/user/11527’: Permission denied
find: ‘./run/chrony’: Permission denied
find: ‘./run/udisks2’: Permission denied
bandit6@bandit:/$ cat ./var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
bandit6@bandit:/$ cat ./etc/bandit_pass/bandit7
cat: ./etc/bandit_pass/bandit7: Permission denied
~~~
looked through the files and found the file which gave me the correct password.

