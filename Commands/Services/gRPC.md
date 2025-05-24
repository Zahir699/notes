```
Running and using grpcui:
sudo apt remove golang-go
wget https://go.dev/dl/go1.24.3.linux-amd64.tar.gz
sudo tar -C /usr/local/ -xzf go1.24.3.linux-amd64.tar.gz 
export PATH=$PATH:/usr/local/go/bin
source ~/.bashrc
go version
go run /home/zahir06/grpcui/cmd/grpcui/grpcui.go -plaintext 10.129.70.157:50051

Using grpcurl:
wget https://github.com/fullstorydev/grpcurl/releases/download/v1.9.3/grpcurl_1.9.3_linux_amd64.deb
sudo dpkg -i grpcurl_1.9.3_linux_amd64.deb
grpcurl -plaintext 10.10.11.214:50051 list
grpcurl -plaintext 10.10.11.214:50051 list SimpleApp

```