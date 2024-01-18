 - [x] Key 2
with the word press dashboard we can put in a php [[Reverse Shell]] through the themes, if we go to themes and editor and edit the error 404 theme we can get a rev shell, in the home directory we find a key and a password has we do not have permissions to read the key so we can crack the password hash with [[md5 hash cracker]] which allows us to login to the robot user and cat the key, this isnt root however
- [x] Key 3
using the command find / -perm /4000 we can see nmap has root perms, using [[GTFOBins]] we can see that we can run it with --interactive and run !sh to get a root shell allowing us to cat the key in the root dir
