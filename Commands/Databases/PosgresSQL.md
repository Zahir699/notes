```
Connecting to the database on a local port forwarded port.

psql -h localhost -p 10000 -U christine

Navigating the database

\l : list databases
\c <database name> : connect to a database
\dt : list the database's tables
SELECT * FROM flag; : select all information from the table called flag
```