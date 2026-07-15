# Manual

## Unix Shell

Install according to your package manager.

![[Core Utilities#^978eed]]

Generate QRCode.

```
$ qrencode "<string>" -o qrcode.png

$ qrencode "<URL>" -o qrcode.png
```

Display the QRCode in the terminal.

```
$ qrencode -t ANSIUTF8 "<string>"
```

## Website

```
$ curl qrenco.de/http[s]://<attacker_IP>

$ curl https://qrenco.de/http[s]://<attacker_IP>

$ echo "https://<attacker_IP>" | curl https://qrcode.show -d @-

$ curl https://qrcode.show/https://<attacker_IP> -H "Accept: image/png" > qrcode.png
```

---
## References

### Black Hat Ethical Hacking

- [Black Hat Ethical Hacking: How do QR Codes work and how criminal hackers use them to generate phishing attacks - Demo](https://www.blackhatethicalhacking.com/articles/how-do-qr-codes-work-and-how-criminal-hackers-use-them-to-generate-phishing-attacks-demo/)

### Hackers Arise

- [Hackers Arise: Using QRCodes in Phishing and Social Media Attacks](https://hackers-arise.com/cyberwar-mission-3-turning-your-enemies-strength-against-them/)

- [Hackers Arise: Using QRCodes in Phishing and Social Media Attacks](https://hackers-arise.com/cyberwar-mission-3-turning-your-enemies-strength-against-them-2/)