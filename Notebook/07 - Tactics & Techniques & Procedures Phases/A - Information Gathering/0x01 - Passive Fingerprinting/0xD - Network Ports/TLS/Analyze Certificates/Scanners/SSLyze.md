# SSLyze

## 01 - Help Menu

```
$ sslyze -h
usage: sslyze [-h] [--update_trust_stores] [--cert CERTIFICATE_FILE] [--key KEY_FILE] [--keyform KEY_FORMAT] [--pass PASSPHRASE]
              [--json_out JSON_FILE] [--targets_in TARGET_FILE] [--quiet] [--slow_connection] [--https_tunnel PROXY_SETTINGS] [--starttls PROTOCOL]
              [--xmpp_to HOSTNAME] [--sni SERVER_NAME_INDICATION] [--resum] [--resum_attempts RESUM_ATTEMPTS] [--elliptic_curves] [--early_data]
              [--openssl_ccs] [--heartbleed] [--http_headers] [--sslv2] [--compression] [--robot] [--tlsv1_3] [--reneg] [--tlsv1_1] [--certinfo]
              [--certinfo_ca_file CERTINFO_CA_FILE] [--tlsv1_2] [--fallback] [--sslv3] [--tlsv1]
              [--mozilla_config {modern,intermediate,old,disable}]
              [target ...]

SSLyze version 5.2.0

positional arguments:
  target                The list of servers to scan.

options:
  -h, --help            show this help message and exit
  --mozilla_config {modern,intermediate,old,disable}
                        Shortcut to queue various scan commands needed to check the server's TLS configurations against one of Mozilla's recommended
                        TLS configuration. Set to "intermediate" by default. Use "disable" to disable this check.

Trust stores options:
  --update_trust_stores
                        Update the default trust stores used by SSLyze. The latest stores will be downloaded from
                        https://github.com/nabla-c0d3/trust_stores_observatory. This option is meant to be used separately, and will silence any
                        other command line option supplied to SSLyze.

Client certificate options:
  --cert CERTIFICATE_FILE
                        Client certificate chain filename. The certificates must be in PEM format and must be sorted starting with the subject's
                        client certificate, followed by intermediate CA certificates if applicable.
  --key KEY_FILE        Client private key filename.
  --keyform KEY_FORMAT  Client private key format. DER or PEM (default).
  --pass PASSPHRASE     Client private key passphrase.

Input and output options:
  --json_out JSON_FILE  Write the scan results as a JSON document to the file JSON_FILE. If JSON_FILE is set to '-', the JSON output will instead be
                        printed to stdout. The resulting JSON file is a serialized version of the ScanResult objects described in SSLyze's Python
                        API: the nodes and attributes will be the same. See https://nabla-c0d3.github.io/sslyze/documentation/available-scan-
                        commands.html for more details.
  --targets_in TARGET_FILE
                        Read the list of targets to scan from the file TARGET_FILE. It should contain one host:port per line.
  --quiet               Do not output anything to stdout; useful when using --json_out.

Contectivity options:
  --slow_connection     Greatly reduce the number of concurrent connections initiated by SSLyze. This will make the scans slower but more reliable
                        if the connection between your host and the server is slow, or if the server cannot handle many concurrent connections.
                        Enable this option if you are getting a lot of timeouts or errors.
  --https_tunnel PROXY_SETTINGS
                        Tunnel all traffic to the target server(s) through an HTTP CONNECT proxy. HTTP_TUNNEL should be the proxy's URL:
                        'http://USER:PW@HOST:PORT/'. For proxies requiring authentication, only Basic Authentication is supported.
  --starttls PROTOCOL   Perform a StartTLS handshake when connecting to the target server(s). StartTLS should be one of: auto, smtp, xmpp,
                        xmpp_server, pop3, imap, ftp, ldap, rdp, postgres. The 'auto' option will cause SSLyze to deduce the protocol (ftp, imap,
                        etc.) from the supplied port number, for each target servers.
  --xmpp_to HOSTNAME    Optional setting for STARTTLS XMPP. XMPP_TO should be the hostname to be put in the 'to' attribute of the XMPP stream.
                        Default is the server's hostname.
  --sni SERVER_NAME_INDICATION
                        Use Server Name Indication to specify the hostname to connect to. Will only affect TLS 1.0+ connections.

Scan commands:
  --resum               Test a server for TLS 1.2 session resumption support using session IDs and TLS tickets.
  --resum_attempts RESUM_ATTEMPTS
                        To be used with --resum. Number of session resumptions (both with Session IDs and TLS Tickets) that SSLyze should attempt.
                        The default value is 5, but a higher value such as 100 can be used to get a more accurate measure of how often session
                        resumption succeeds or fails with the server.
  --elliptic_curves     Test a server for supported elliptic curves.
  --early_data          Test a server for TLS 1.3 early data support.
  --openssl_ccs         Test a server for the OpenSSL CCS Injection vulnerability (CVE-2014-0224).
  --heartbleed          Test a server for the OpenSSL Heartbleed vulnerability.
  --http_headers        Test a server for the presence of security-related HTTP headers.
  --sslv2               Test a server for SSL 2.0 support.
  --compression         Test a server for TLS compression support, which can be leveraged to perform a CRIME attack.
  --robot               Test a server for the ROBOT vulnerability.
  --tlsv1_3             Test a server for TLS 1.3 support.
  --reneg               Test a server for for insecure TLS renegotiation and client-initiated renegotiation.
  --tlsv1_1             Test a server for TLS 1.1 support.
  --certinfo            Retrieve and analyze a server's certificate(s) to verify its validity.
  --certinfo_ca_file CERTINFO_CA_FILE
                        To be used with --certinfo. Path to a file containing root certificates in PEM format that will be used to verify the
                        validity of the server's certificate.
  --tlsv1_2             Test a server for TLS 1.2 support.
  --fallback            Test a server for the TLS_FALLBACK_SCSV mechanism to prevent downgrade attacks.
  --sslv3               Test a server for SSL 3.0 support.
  --tlsv1               Test a server for TLS 1.0 support.
```

## 02 - Usage

```
$ sslyze <IP_1>,<IP_2>,<IP_n>
```

Scan multiple IP addresses

```
$ sslyze $(cat ip_targets.txt)
```

---
## References

### Source Repositories

- [SSLyze](https://github.com/nabla-c0d3/sslyze)

- [SSLyze Documentation](https://nabla-c0d3.github.io/sslyze/documentation/)