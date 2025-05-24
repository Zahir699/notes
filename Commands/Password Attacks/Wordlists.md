# Create targeted wordlist

```
Crunch:
crunch <minimum length> <maximum length> <charset> -t <pattern> -o <output file>

@ : Lowercase
, : Uppercase
% : Numbers
^ : Symbols

crunch 17 17 -t ILFREIGHT201%@@@@ -o wordlist

-d : Limits the number of duplicate characters.   -d  2@  limits  the lower  case  alphabet to output like aab and aac.  aaa would not be generated as that is 3 consecutive letters of a.

crunch 12 12 -t 10031998@@@@ -d 1 -o wordlist

```


# CUPP
```
python3 cupp.py -i
```


## Princeprocessor
```
wget https://github.com/hashcat/princeprocessor/releases/download/v0.22/princeprocessor-0.22.7z ; 7z x princeprocessor-0.22.7z ; cd princeprocessor-0.22

Make wordlist with two or three words or as many as you want
Find the number combinations:
./pp64.bin --keyspace < wordlist.txt

Set password length limits:
./pp64.bin --pw-min=10 --pw-max=25 -o wordlist.txt < wordlist.txt

Set amount of elements per word  i.e.," dogdogdog`." :
./pp64.bin --elem-cnt-min=3 -o wordlist.txt < wordlist.txt

```


# CeWL
```
cewl -d <depth to spider> -m <minimum word length> -w <output wordlist> <url of website>

cewl -d 5 -m 8 -e http://inlanefreight.com/blog -w wordlist.txt

-e : Extraction of emails from websites.
```


# Hashcat-utils
```
wget https://github.com/hashcat/maskprocessor/releases/download/v0.73/maskprocessor-0.73.7z ; 7z x maskprocessor-0.73.7z ; cd maskprocessor-0.73/ 

./mp64.bin Welcome?s

Create targeted wordlist with hashcat mask options.
```
