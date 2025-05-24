```
Look for files to exploit:
find / -user root -perm -4000 -exec ls -ldb {} \; 2>/dev/null
find / -user root -perm -6000 -exec ls -ldb {} \; 2>/dev/null

Once found identify how to exploit in GTFOBins


```