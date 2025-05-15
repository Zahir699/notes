1. Connecting to a MySQL database
```
mysql -u <user> -h <ip of database>
-h : Connect to host.
-u : User for log-in if not current user.

====================================================================
<<<<<<<<<<<<<<<<<<<<<<<<Navigating the databse>>>>>>>>>>>>>>>>>>>>>

SHOW databases; : Prints out the databases we can access. 

USE {database_name}; : Set to use the database named {database_name}. 

SHOW tables; : Prints out the available tables inside the current database. 

SELECT * FROM {table_name}; : Prints out all the data from the table {table_name}.

```