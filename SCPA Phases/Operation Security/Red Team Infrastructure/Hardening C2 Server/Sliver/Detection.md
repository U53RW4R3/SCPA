# Sliver

Search Tag(s): #red-team-infrastructure #sliver #detection

## 01 - Shodan

`ssl:multiplayer ssl:operators`

## 02 - JARM

- To scan for MTLS listener.

```
$ git clone https://github.com/salesforce/jarm.git

$ cd jarm/

$ python jarm.py <C2_IP> -p 8888
```

 - To scan for HTTP/HTTPS listener.

```
$ python jarm.py <C2_IP> -p 443

$ python jarm.py <C2_IP> -p 80
```

---
## References

- [drb-ra: C2IntelFeeds](https://github.com/drb-ra/C2IntelFeeds)

- [Hunting C2 with Shodan](https://michaelkoczwara.medium.com/hunting-c2-with-shodan-223ca250d06f)

- [Detecting Sliver C2 framework with Wazuh](https://wazuh.com/blog/detecting-sliver-c2-framework-with-wazuh/)

- [C2 JARM](https://github.com/cedowens/C2-JARM)

- [JARM](https://github.com/salesforce/jarm)