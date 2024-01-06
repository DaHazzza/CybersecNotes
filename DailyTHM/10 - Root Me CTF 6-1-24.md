First we start with a simple [[Nmap]] and find 2 ports 80 http and 22 ssh

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))

then we cna use [[Gobuster]] to enumerate directories
we find /panel/ as a hidden directory which allows up to upload hidden files

we can upload a php reverse shel;l but .php files are invalid so we can use the .phtml extension 

now looking in the home directory we can ind a file with the flag THM{y0u_g0t_a_sh3ll}

now we need to try privlidge esculate

