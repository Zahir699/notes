For querying the ldap server for information about the user "support"
```
ldapsearch -x -H ldap://support.htb -D "ldap@support.htb" -w 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' -b "dc=support,dc=htb" "(cn=support)"

-H : is for specifying the server URL (instead of `-h`).
-x : is used for simple authentication (no SASL).
-D : user@domain.com
-w : user password
-b "dc=domain,dc=com"
cn=<account we want to query about>
```

# Querying LDAP with ApacheDirectoryStudio
```
## Install the utility

wget https://dlcdn.apache.org/directory/studio/2.0.0.v20210717-M17/ApacheDirectoryStudio-2.0.0.v20210717-M17-linux.gtk.x86_64.tar.gz 

tar xfz ApacheDirectoryStudio-2.0.0.v20210717-M17-linux.gtk.x86_64.tar.gz

1. run it
2. Next, let's add a connection to the LDAP server by clicking the LDAP button on the top left of the screen.
3. In this new page right click anywhere inside the Connections window and select New Connection .
4. Input Support as the connection name, <domain.com> as the hostname and click Next
5. In the next window make sure to select Simple Authentication as the authentication method, ldap@support.htb as the Bind DN and paste in the password in the Bind password field. Then click the Check Authentication button to make sure that everything works properly.
```