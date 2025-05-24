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

- '?a' -> All ascii characters

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


# Rules

| **Function**    | **Description**                                                    | **Input**                             | **Output**                                                                                                        |
| --------------- | ------------------------------------------------------------------ | ------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| l               | Convert all letters to lowercase                                   | InlaneFreight2020                     | inlanefreight2020                                                                                                 |
| u               | Convert all letters to uppercase                                   | InlaneFreight2020                     | INLANEFREIGHT2020                                                                                                 |
| c / C           | capitalize / lowercase first letter and invert the rest            | inlaneFreight2020 / Inlanefreight2020 | Inlanefreight2020 / iNLANEFREIGHT2020                                                                             |
| t / TN          | Toggle case : whole word / at position N                           | InlaneFreight2020                     | iNLANEfREIGHT2020                                                                                                 |
| d / q / zN / ZN | Duplicate word / all characters / first character / last character | InlaneFreight2020                     | InlaneFreight2020InlaneFreight2020 / IInnllaanneeFFrreeiigghhtt22002200 / IInlaneFreight2020 / InlaneFreight20200 |
| { / }           | Rotate word left / right                                           | InlaneFreight2020                     | nlaneFreight2020I / 0InlaneFreight202                                                                             |
| ^X / $X         | Prepend / Append character X                                       | InlaneFreight2020 (^! / $! )          | !InlaneFreight2020 / InlaneFreight2020!                                                                           |
| r               | Reverse                                                            | InlaneFreight2020                     | 0202thgierFenalnI                                                                                                 |
| s               | Replace                                                            | Password (ss$)                        | Pa$$word                                                                                                          |

```
Create rule file:
echo 'c so0 si1 se3 ss5 sa@ $2 $0 $1 $9' > rule.txt
echo 'password_ilfreight' > test.txt

Debug the rule:
hashcat -r rule.txt test.txt --stdout

Create hash:
echo -n 'St@r5h1p2019' | sha1sum | awk '{print $1}' | tee hash

Crack:
hashcat -a 0 -m 100 hash /opt/useful/seclists/Passwords/Leaked-Databases/rockyou.txt -r rule.txt

Default rules folder:
ls -lart /usr/share/hashcat/rules/

Generate random rules:
hashcat -a 0 -m 100 -g 1000 hash /usr/share/wordlists/rockyou.txt.gz

```


# Common hashes
```
1. MD5, SHA1, and bcrypt
Generate hashes:
for i in $(cat words); do echo -n $i | sha1sum | tr -d ' -';done

2 Linux shadow file:
root:$6$tOA0cyybhb/Hr7DN$htr2vffCWiPGnyFOicJiXJVMbk1muPORR.eRGYfBYUnNPUjWABGPFiphjIjJC5xPfFUASIbVKDAHS3vTW1qU.1:18285:0:99999:7:::

Actual password field:
$6$tOA0cyybhb/Hr7DN$htr2vffCWiPGnyFOicJiXJVMbk1muPORR.eRGYfBYUnNPUjWABGPFiphjIjJC5xPfFUASIbVKDAHS3vTW1qU.1

Crack:
hashcat -m 1800 nix_hash /usr/share/wordlists/rockyou.txt

3. Windows hashes
   NTLM hashes --> -m 1000
   NTLMv2 hashes --> -m 5600
```


# Cracking files hashes

```
Microsoft office documents:

|**Mode**|**Target**|
|---|---|
|`9400`|MS Office 2007|
|`9500`|MS Office 2010|
|`9600`|MS Office 2013|

python office2john.py hashcat_Word_example.docx

Zip files:

|**Mode**|**Target**|
|---|---|
|`11600`|7-Zip|
|`13600`|WinZip|
|`17200`|PKZIP (Compressed)|
|`17210`|PKZIP (Uncompressed)|
|`17220`|PKZIP (Compressed Multi-File)|
|`17225`|PKZIP (Mixed Multi-File)|
|`17230`|PKZIP (Compressed Multi-File Checksum-Only)|
|`23001`|SecureZIP AES-128|
|`23002`|SecureZIP AES-192|
|`23003`|SecureZIP AES-256|

zip2john blueprints.zip
7z2john hashcat.7z > zip.hash

hashcat -a 0 -m 11600 zip.hash /usr/share/wordlists/rockyou.txt.gz


Keepass files:

|**Mode**|**Target**|
|---|---|
|`13400`|KeePass 1 AES / without keyfile|
|`13400`|KeePass 2 AES / without keyfile|
|`13400`|KeePass 1 Twofish / with keyfile|
|`13400`|Keepass 2 AES / with keyfile|

python keepass2john.py Master.kdbx 
hashcat -a 0 -m 13400 keepass_hash /opt/useful/seclists/Passwords/Leaked-Databases/rockyou.txt

PDF files:
Download the script at:
[raw.githubusercontent.com/truongkma/ctf-tools/master/John/run/pdf2john.py](https://raw.githubusercontent.com/truongkma/ctf-tools/master/John/run/pdf2john.py)

python pdf2john.py inventory.pdf | awk -F":" '{ print $2}'

|**Mode**|**Target**|
|---|---|
|`10400`|PDF 1.1 - 1.3 (Acrobat 2 - 4)|
|`10410`|PDF 1.1 - 1.3 (Acrobat 2 - 4), collider #1|
|`10420`|PDF 1.1 - 1.3 (Acrobat 2 - 4), collider #2|
|`10500`|PDF 1.4 - 1.6 (Acrobat 5 - 8)|
|`10600`|PDF 1.7 Level 3 (Acrobat 9)|
|`10700`|PDF 1.7 Level 8 (Acrobat 10 - 11)|

hashcat -a 0 -m 10500 pdf_hash /opt/useful/seclists/Passwords/Leaked-Databases/rockyou.txt

Vmware virtual machines:
python3 vmwarevmx2hashcat.py --vmx ILF-MS01.vmx
hashcat -a 3 -m 27400 vmx.hash Inlane_?a?a?a

```



# Cracking wireless handshakes
```
1. Cracking MIC:
git clone https://github.com/hashcat/hashcat-utils.git ; cd hashcat-utils/src ; make

Converto from cap to hcxpcap:
[hashcat hcxpcapngtool - advanced password recovery](https://hashcat.net/cap2hashcat/)

or..

./cap2hccapx.bin corp_capture1-01.cap <output file>.hccapx

hashcat -a 0 -m 22000 mic_to_crack.hccapx /opt/useful/seclists/Passwords/Leaked-Databases/rockyou.txt

2. Cracking PMKID:

git clone https://github.com/ZerBea/hcxtools.git ; cd hcxtools ; make && make install

hcxpcapngtool cracking_pmkid.cap -o pmkidhash_corp

hashcat -a 0 -m 22000 pmkidhash_corp /opt/useful/seclists/Passwords/Leaked-Databases/rockyou.txt.tar.gz


```