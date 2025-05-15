# Vhost Fuzzing

```
ffuf -w /opt/useful/seclists/Discovery/DNS/subdomains-top1million-20000.txt:FUZZ -u http://thetoppers.htb/ -H 'Host: FUZZ.thetoppers.htb'  -s -fs 11952

-w : wordlist to use
-u : url
-H : Host header information containing the fuzzed subdomains
-s : silent
-fs : filter by size
```

# Directory Fuzzing

```
ffuf -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3 medium.txt:FFUZ -u http://dev.devvortex.htb/FFUZ -ic  -t 100
```