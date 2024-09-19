# Amass

### Setup

```
$ go install github.com/owasp-amass/amass/v3/...@master && \
sudo mv ~/go/bin/amass /usr/local/bin
```

### Usage

```
$ amass intel -d <domain.com> -whois

$ amass intel -whois -d <website.com> -dir whois-output
```