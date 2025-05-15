# Directory Fuzzing

```
gobuster dir -u http://10.129.123.161/ -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-small.txt -t 100 -x .php
```
```
	dir << directory fuzzing
		-w << path to wordlist
		-t << parallel threads
		-x << suffix of php e.g. admin<.php>
```


# Vhost Fuzzing

```
gobuster vhost -w /opt/useful/seclists/Discovery/DNS/subdomains-top1million-5000.txt -u http://thetoppers.htb

**Add the main domain to the corresponding IP to the /etc/hosts file

vhost : Uses VHOST for brute-forcing
-w   : Path to the wordlist
-u   : Specify the URL
```