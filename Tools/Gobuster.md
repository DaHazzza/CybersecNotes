Gobuster is a tool used to brute-force URIs including directories and files as well as DNS subdomains.

## gobuster Usage Examples

Scan a website (`-u http://192.168.0.155/`) for directories using a wordlist (`-w /usr/share/wordlists/dirb/common.txt`) and print the full URLs of discovered paths (`-e`):

`gobuster -e -u http://192.168.0.155/ -w /usr/share/wordlists/dirb/common.txt
