# Amass

### Setup

```
$ go install -v github.com/owasp-amass/amass/v3/...@master && \
sudo cp ~/go/bin/amass /usr/local/bin
```

### Usage

`$ amass intel -whois -d <website.com> -dir whois-output`