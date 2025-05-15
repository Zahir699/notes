1. Default port is 873
2. Connecting to rsync server
```
rsync [OPTION] … [USER@]HOST::SRC [DEST]

rsync --list-only {target_IP}:: << list available "shares"

rsync --list-only {target_IP}::public << list contents of a share

rsync {target_IP}::public/flag.txt flag.txt << copying a file to our box

```