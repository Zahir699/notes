```
Get the binary and apply appropriate perms:
wget https://github.com/DominicBreuker/pspy/releases/download/v1.2.1/pspy64 ; chmod +x pspy64

Usage:
-p: enables printing commands to stdout (enabled by default)
-f: enables printing file system events to stdout (disabled by default)
-r: list of directories to watch with Inotify. pspy will watch all subdirectories recursively (by default, watches /usr, /tmp, /etc, /home, /var, and /opt).
-d: list of directories to watch with Inotify. pspy will watch these directories only, not the subdirectories (empty by default).
-i: interval in milliseconds between procfs scans. pspy scans regularly for new processes regardless of Inotify events, just in case some events are not received.
-c: print commands in different colors. File system events are not colored anymore, commands have different colors based on process UID.
--debug: prints verbose error messages which are otherwise hidden.

Example:
./pspy64 -pf -i 1000

```