there are many methods to get a reverse shell using a [[Reverse Shell Generator]], 
ince we have a rev shell we can stabalse it using python 
```bash
python -c 'import pty; pty.spawn("/bin/bash")'
```