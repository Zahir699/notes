Find a sudo or SUID binary that can run as root
```
1. Create a file like 'cat' in the /tmp folder with /bin/sh as contents
2. export PATH=/tmp:$PATH
3. Run the vulnerable SUID, if its executed as root it will spawn a root shell.

```