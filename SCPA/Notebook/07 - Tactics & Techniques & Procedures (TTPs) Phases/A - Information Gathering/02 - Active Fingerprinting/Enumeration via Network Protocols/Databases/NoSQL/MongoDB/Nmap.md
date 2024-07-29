# Nmap

TODO: Fill this info

```
$ nmap -p 27017,27018 -Pn --script mongodb-databases <IP>

$ nmap -p 27017,27018 -Pn --script mongodb-info <IP>
```

```
$ nmap -p 27017,27018 -Pn -sV --script "mongo* and default" <IP>
```