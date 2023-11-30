# Setup

Search Tag(s): #red-team-infrastructure #covenant

TODO: Provide examples for setting Covenant C2 by changing profiles, adding firewalls, domain fronting, etc

### HTTP

```
$ sudo a2enmod rewrite proxy proxy_http proxy_connect headers && \
sudo systemctl restart apache2
```

---
## References

- [Hunting C2 with Shodan](https://michaelkoczwara.medium.com/hunting-c2-with-shodan-223ca250d06f)