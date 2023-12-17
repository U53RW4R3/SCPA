# Nmap

```
$ nmap -p80,443 -Pn -n --script http-waf-detect <IP>

$ nmap -p80,443 -Pn -n --script http-waf-detect <IP> --script-args="http-waf-detect.aggro,http-waf-detect.uri=/<URL>/index.php" <IP>

$ nmap -p80,443 -Pn -n --script http-waf-fingerprint <IP>

$ nmap -p80,443 -Pn -n --script http-waf-fingerprint --script-args http-waf-fingerprint.intensive=1 <IP`
```