1. Default port 6379
2. Connect using redis-cli
```
   connect with  "redis-cli -h 10.129.123.162 -a <Password here>"
```
1. Move around
```
   **info** << retrieve information and statistics about the database
   **keyspace** << enumerate available databases and its keys
   **select 0** << select database
   **keys ** << list all keys in a database
   **get <key>**  << retrieve a specific key
```