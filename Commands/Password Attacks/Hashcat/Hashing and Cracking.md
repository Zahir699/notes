```
Create a hash:
echo -n "HackTheBox123!" | md5sum

Identify hash type:
hashid '$DCC2$10240#tom#e4e938d12fe5974dc42a90120bd9c90f' -m
hashcat --show '$S$D34783772bRXEx1aCsvY.bqgaaSu75XmVlKrW9Du8IQlvxHlmzLc'

[[example_hashes [hashcat wiki]](https://hashcat.net/wiki/doku.php?id=example_hashes)]()


```


# Dictionary attack 
```
Syntax:
hashcat -a 0 -m <hash type> <hash file> <wordlist>
Example:
hashcat -a 0 -m 0 md5hash.txt /usr/share/wordlists/rockyou.txt.gz

```


# Combination attack
```
See what hashcat will produce:
hashcat -a 1 --stdout file1 file2

Syntax:
hashcat -a 1 -m <hash type> <hash file> <wordlist1> <wordlist2>

Example:
hashcat -a 1 -m 0 combination_md5 wordlist1 wordlist2
```


# Mask Attack
```
Create hash:
echo -n "Solarislol99##" | md5sum | cut -f1 -d ' ' > trisolaris.txt

Crack hash:
hashcat -a 3 -m 0 trisolaris.txt -1 '#' 'Solar?l?l?l?l?l?d?d?1?1'

-a 3 : Mask attack mode (Brute Force)
-1 : Defines custom charsets, it creates custome placeholders with specific set of characters meaning it wont have to brute force or guess that placeholder, in this case i defined it to be # which means it will put that char on every iteration.

- `?l` → lowercase letters
    
- `?u` → uppercase letters
    
- `?d` → digits
    
- `?s` → special characters

- '?[1-4]' --> can set 4 placeholders, !! they can be anything

```

# Hybrid attack
```
echo -n 'football1$' | md5sum | tr -d " -" > hybrid_hash

Append to the end of the word:
hashcat -a 6 -m 0 hybrid_hash /opt/useful/seclists/Passwords/Leaked-Databases/rockyou.txt '?d?s'

Prepend to the beginning of the word:
hashcat -a 7 -m 0 hybrid_hash_prefix -1 01 '20?1?d' /opt/useful/seclists/Passwords/Leaked-Databases/rockyou.txt

```

