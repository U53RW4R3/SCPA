# MongoDB

TODO: Fill this info

## 01 - Authentication

```
$ mongosh
```

```
$ nmap -p 27017,27018 -Pn --script mongodb-databases <IP>

$ nmap -p 27017,27018 -Pn --script mongodb-info <IP>
```

```
$ nmap -p 27017,27018 -Pn -sV --script "mongo* and default" <IP>
```

```
$ nuclei -l ip_targets.txt -t ~/nuclei-templates -id mongodb-info-enum
```

## Databases

```
> show dbs

> use <database>
```

## Tables

```
> show collections

> show tables
```

## Query

```
> db.<table>.find()
```

---
## References

### Hacktricks

- [Hacktricks: Pentesting MongoDB](https://book.hacktricks.wiki/en/network-services-pentesting/27017-27018-mongodb.html)