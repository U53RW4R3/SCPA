# Amass

### Setup

```
$ go install github.com/owasp-amass/amass/v3/...@master && \
sudo mv ~/go/bin/amass /usr/local/bin
```

### Usage

```
$ amass intel -whois -d domain.tld

$ amass intel -whois -d domain.tld -dir whois-output
```