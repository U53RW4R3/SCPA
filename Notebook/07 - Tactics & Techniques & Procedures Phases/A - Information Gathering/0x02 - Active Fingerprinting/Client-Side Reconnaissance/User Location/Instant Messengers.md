# Instant Messengers

Track someone's public IP address when interacting through text messaging (e.g.: Whatsapp).

```
# tshark -i <interface> -f "udp" -Y "stun.type == 0x0101 && stun.att.type == 0x0020 && stun.att.ipv4 != <your_public_IP>" -T fields -e stun.att.ipv4
```