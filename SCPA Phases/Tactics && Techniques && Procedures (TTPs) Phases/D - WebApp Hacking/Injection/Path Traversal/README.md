# Description

Search Tag(s): #path-traversal

TODO: Fill this description about Path Traversal

```php
<?php
$file = $_GET['file'];
if(isset($file)) {
	include($file);
}
?>
```

---
## References

- [Portswigger: File Path Traversal](https://portswigger.net/web-security/file-path-traversal)

- [Hacktricks: File Inclusion](https://book.hacktricks.xyz/pentesting-web/file-inclusion)

- [File Path Traversal and File Inclusions](https://asfiyashaikh.medium.com/file-path-traversal-and-file-inclusions-7c567da9e226)

- [NetSPI: Directory Traversal File Inclusion Proc Filesystem](https://www.netspi.com/blog/technical/web-application-penetration-testing/directory-traversal-file-inclusion-proc-file-system/)

- [Highon Coffee LFI Cheatsheet](https://highon.coffee/blog/lfi-cheat-sheet/)

- [Enumerating Linux Processes Through LFI](https://tun0.blog/posts/pidlfi/)

- [Invicti Local File Inclusion](https://www.invicti.com/learn/local-file-inclusion-lfi/)