# FingerprintJS

https://developers.whatismybrowser.com

```php
<?php
$data = "Client IP Address: " . $_SERVER['REMOTE_ADDR'] . "\n";
$data .= file_get_contents('php://input');
$data .= "---------------------------------\n\n";
file_put_contents('/var/www/html/fp/fingerprint.txt', print_r($data, true), FILE_APPEND | LOCK_EX);
?>
```

```
$ sudo chown www-data:www-data /var/www/html/fp
```

---
## References

- [FingerprintJS](https://github.com/fingerprintjs/fingerprintjs)