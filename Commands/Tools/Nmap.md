```
Scan quickly all ports:
ports=$(nmap -p- --min-rate=1000 -T4 [IP] | grep '^[0-9]' | cut -d '/' -f 1 | tr '\n' ',' | sed s/,$//) 
nmap -p$ports -sC -sV [IP]
```