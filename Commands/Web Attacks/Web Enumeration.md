```
1. Direcotyr and file enumeration:
gobuster dir -u http://10.10.10.121/ -w /usr/share/seclists/Discovery/Web-Content/common.txt

2. Dns enumeration:
gobuster dns -d inlanefreight.com -w /usr/share/SecLists/Discovery/DNS/namelist.txt

3. Vhost enumeration:
gobuster vhost -u http://10.10.10.121/ -w /usr/share/seclists/Discovery/Web-Content/common.txt

4. Banner grab / web server header, vist the website:
curl -IL https://www.inlanefreight.com

5. Extract the version of web servers, supporting frameworks, and applications:
whatweb 10.10.10.121
whatweb --no-errors 10.10.10.121/24

6. Check for directory listing, robots.txt and source code.


```