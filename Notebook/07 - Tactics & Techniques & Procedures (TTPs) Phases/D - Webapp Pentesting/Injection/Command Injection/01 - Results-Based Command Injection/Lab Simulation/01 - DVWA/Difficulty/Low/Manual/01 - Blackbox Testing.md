# 01 - Blackbox Testing

Search Tag(s): #command-injection #dvwa

```php
<?php
echo '<pre>';
$IP_address = $_GET["IP_address"];
$ping = shell_exec("ping " . $IP_address);
echo($ping);
echo '</pre>';
?>
```

## Enumeration

### Web Root Directory

---
## References

- [Command Injection Vulnerabilities Exploitation Case Study](https://resources.infosecinstitute.com/topics/secure-coding/command-injection-vulnerabilities-exploitation-case-study/)