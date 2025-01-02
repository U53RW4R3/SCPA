# SSLScan

## Help Menu

```
$ sslscan -h 
                   _
           ___ ___| |___  ___ __ _ _ __
          / __/ __| / __|/ __/ _` | '_ \
          \__ \__ \ \__ \ (_| (_| | | | |
          |___/___/_|___/\___\__,_|_| |_|


                2.1.2-static
                OpenSSL 3.0.12 24 Oct 2023


Command:
  sslscan [options] [host:port | host]

Options:
  --targets=<file>     A file containing a list of hosts to check.
                       Hosts can  be supplied  with ports (host:port)
  --sni-name=<name>    Hostname for SNI
  --ipv4, -4           Only use IPv4
  --ipv6, -6           Only use IPv6

  --show-certificate   Show full certificate information
  --show-client-cas    Show trusted CAs for TLS client auth
  --no-check-certificate  Don't warn about weak certificate algorithm or keys
  --ocsp               Request OCSP response from server
  --pk=<file>          A file containing the private key or a PKCS#12 file
                       containing a private key/certificate pair
  --pkpass=<password>  The password for the private  key or PKCS#12 file
  --certs=<file>       A file containing PEM/ASN1 formatted client certificates

  --ssl2               Only check if SSLv2 is enabled
  --ssl3               Only check if SSLv3 is enabled
  --tls10              Only check TLSv1.0 ciphers
  --tls11              Only check TLSv1.1 ciphers
  --tls12              Only check TLSv1.2 ciphers
  --tls13              Only check TLSv1.3 ciphers
  --tlsall             Only check TLS ciphers (all versions)
  --show-ciphers       Show supported client ciphers
  --show-cipher-ids    Show cipher ids
  --iana-names         Use IANA/RFC cipher names rather than OpenSSL ones
  --show-times         Show handhake times in milliseconds

  --no-cipher-details  Disable EC curve names and EDH/RSA key lengths output
  --no-ciphersuites    Do not check for supported ciphersuites
  --no-compression     Do not check for TLS compression (CRIME)
  --no-fallback        Do not check for TLS Fallback SCSV
  --no-groups          Do not enumerate key exchange groups
  --no-heartbleed      Do not check for OpenSSL Heartbleed (CVE-2014-0160)
  --no-renegotiation   Do not check for TLS renegotiation
  --show-sigs          Enumerate signature algorithms

  --starttls-ftp       STARTTLS setup for FTP
  --starttls-imap      STARTTLS setup for IMAP
  --starttls-irc       STARTTLS setup for IRC
  --starttls-ldap      STARTTLS setup for LDAP
  --starttls-mysql     STARTTLS setup for MYSQL
  --starttls-pop3      STARTTLS setup for POP3
  --starttls-psql      STARTTLS setup for PostgreSQL
  --starttls-smtp      STARTTLS setup for SMTP
  --starttls-xmpp      STARTTLS setup for XMPP
  --xmpp-server        Use a server-to-server XMPP handshake
  --rdp                Send RDP preamble before starting scan

  --bugs               Enable SSL implementation bug work-arounds
  --no-colour          Disable coloured output
  --sleep=<msec>       Pause between connection request. Default is disabled
  --timeout=<sec>      Set socket timeout. Default is 3s
  --connect-timeout=<sec>  Set connect timeout. Default is 75s
  --verbose            Display verbose output
  --version            Display the program version
  --xml=<file>         Output results to an XML file. Use - for STDOUT.
  --help               Display the help text you are now reading

Example:
  sslscan 127.0.0.1
  sslscan [::1]
```

## Usage

```
$ sslscan <IP>
```

Scan multiple IP addresses

```
$ sslscan --targets=ip_targets.txt
```

Gather subdomains

```
$ sslscan --show-certificate <URL> | tee tls-dns-certificate-output.txt

$ grep "Altnames:" tls-dns-certificate-output.txt | grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' | sort -u > subdomains-output.txt
```

---
## References

- [SSLScan Source Repository](https://github.com/DinoTools/sslscan/)

- [[Domains]]