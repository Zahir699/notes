```
1. Find:
   
find / -type f -name *.conf -user root -size +20k -newermt 2020-03-03 -exec ls -al {} \; 2>/dev/null
-type f : We are looking for a file or 'd' for directory
-user root : Owner is root
-size +20k : can be used together with another -size parameter, can also be negative for 'less than' expressions.
-newermt <date> : Modified time is newer than.
-exec : execute a command.

2. Grep:

cat /etc/passwd | grep -v "false\|nologin"
-v : exclude matches

3. Cut:

cat /etc/passwd | grep -v "false\|nologin" | cut -d":" -f1
-d ':' : sets delimeter to be the colon
-f1 : print field 1, it can be any applicable field

4. Tr:

cat /etc/passwd | grep -v "false\|nologin" | tr ":" " "
":" " " : replace all colon with a space.

5. Column:

cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | column -t
-t : display output in table format

6. Awk:

cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | awk '{print $1, $NF}'
$1 : prints first field
$NF : prints last field

7. Sed:

cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | sed 's/bin/HTB/g'
's/bin/HTB/g' : replace word bin with HTB

8. Wc

cat /etc/passwd | wc -l
-l : count all lines



```