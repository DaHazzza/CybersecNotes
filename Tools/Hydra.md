Hydra is used to brute force passwords on things like http forms and ssh
## hydra Usage Example

Attempt to login as the root user (`-l root`) using a password list (`-P /usr/share/wordlists/metasploit/unix_passwords.txt`) with 6 threads (`-t 6`) on the given SSH server (`ssh://192.168.1.123`):

```bash
root@kali:~# hydra -l root -P /usr/share/wordlists/metasploit/unix_passwords.txt 
```

`hydra -l '' -P 3digits.txt -f -v 10.10.145.239 http-post-form "/login.php:pin=^PASS^:Access denied" -s 8000`

The command above will try one password after another in the `3digits.txt` file. It specifies the following:

- `-l ''` indicates that the login name is blank as the security lock only requires a password
- `-P 3digits.txt` specifies the password file to use
- `-f` stops Hydra after finding a working password
- `-v` provides verbose output and is helpful for catching errors
- `10.10.145.239` is the IP address of the target
- `http-post-form` specifies the HTTP method to use
- `"/login.php:pin=^PASS^:Access denied"` has three parts separated by `:`
    - `/login.php` is the page where the PIN code is submitted
    - `pin=^PASS^` will replace `^PASS^` with values from the password list (also can use ^USER^ for -l)
    - `Access denied` indicates that invalid passwords will lead to a page that contains the text “Access denied”
- `-s 8000` indicates the port number on the target
