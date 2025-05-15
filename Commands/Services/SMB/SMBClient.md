1.  List shares anonymously 
```
    smbclient -L //10.129.123.139 -N
```
1. Connect to share anonymously
```
    smbclient //10.129.123.139/WorkShares -N
```

	Connect with no password
```
	smbclient \\\\10.129.38.203\\C$ -U administrator -P""
```