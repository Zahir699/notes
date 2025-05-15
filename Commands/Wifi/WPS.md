# Enumeration

```
Understand the network topology!!!!

systemctl status wpa_supplicant.service ----> identify which interface is acting as the Access Point, this is important!!!.

systemctl status hostapd.service -----> commonly used service to manage access points

iwconfig
master : configured access point
client : connects to another wireless network as a wifi client
monitor : used for monitoring and testing porpuses
managed : it behaves like a regular client device

iw dev ----> list wireless interface information
phy0 : usually associated with the access point

## retrieve bssid of Access Point and channel information

reaver -i mon0 -b 02:00:00:00:00:00 -vv -c 1
-i : interface
-b : bssid
-c : channel
-vv : verbose
```