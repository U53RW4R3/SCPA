# Gobuster

TODO: Fill this info

## Help Menu

```
$ gobuster dir -h                                                                            
Uses directory/file enumeration mode

Usage:
  gobuster dir [flags]

Flags:
  -f, --add-slash                         Append / to each request
      --client-cert-p12 string            a p12 file to use for options TLS client certificates
      --client-cert-p12-password string   the password to the p12 file
      --client-cert-pem string            public key in PEM format for optional TLS client certificates
      --client-cert-pem-key string        private key in PEM format for optional TLS client certificates (this key needs to have no password)
  -c, --cookies string                    Cookies to use for the requests
  -d, --discover-backup                   Also search for backup files by appending multiple backup extensions
      --exclude-length string             exclude the following content lengths (completely ignores the status). You can separate multiple lengths by comma and it also supports ranges like 203-206
  -e, --expanded                          Expanded mode, print full URLs
  -x, --extensions string                 File extension(s) to search for
  -X, --extensions-file string            Read file extension(s) to search from the file
  -r, --follow-redirect                   Follow redirects
  -H, --headers stringArray               Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2'
  -h, --help                              help for dir
      --hide-length                       Hide the length of the body in the output
  -m, --method string                     Use the following HTTP method (default "GET")
      --no-canonicalize-headers           Do not canonicalize HTTP header names. If set header names are sent as is.
  -n, --no-status                         Don't print status codes
  -k, --no-tls-validation                 Skip TLS certificate verification
  -P, --password string                   Password for Basic Auth
      --proxy string                      Proxy to use for requests [http(s)://host:port] or [socks5://host:port]
      --random-agent                      Use a random User-Agent string
      --retry                             Should retry on request timeout
      --retry-attempts int                Times to retry on request timeout (default 3)
  -s, --status-codes string               Positive status codes (will be overwritten with status-codes-blacklist if set). Can also handle ranges like 200,300-400,404.
  -b, --status-codes-blacklist string     Negative status codes (will override status-codes if set). Can also handle ranges like 200,300-400,404. (default "404")
      --timeout duration                  HTTP Timeout (default 10s)
  -u, --url string                        The target URL
  -a, --useragent string                  Set the User-Agent string (default "gobuster/3.6")
  -U, --username string                   Username for Basic Auth

Global Flags:
      --debug                 Enable debug output
      --delay duration        Time each thread waits between requests (e.g. 1500ms)
      --no-color              Disable color output
      --no-error              Don't display errors
  -z, --no-progress           Don't display progress
  -o, --output string         Output file to write results to (defaults to stdout)
  -p, --pattern string        File containing replacement patterns
  -q, --quiet                 Don't print the banner and other noise
  -t, --threads int           Number of concurrent threads (default 10)
  -v, --verbose               Verbose output (errors)
  -w, --wordlist string       Path to the wordlist. Set to - to use STDIN.
      --wordlist-offset int   Resume from a given position in the wordlist (defaults to 0)
```

## Usage

`$ gobuster dir -u <URL> --random-agent -t 32 -w wordlist.txt -e php,txt,sh -x 404 -o output.txt`

---
## References

- [Tutorial for Gobuster Tool](https://sitechsecurity.wordpress.com/2020/07/14/tutorial-for-gobuster-tool/)