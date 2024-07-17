# TestSSL

## 01 - Help Menu

```
$ testssl   

     "testssl [options] <URI>"    or    "testssl <options>"

"testssl <option>", where <option> is mostly standalone and one of:

     --help                        what you're looking at
     -b, --banner                  displays banner + version of testssl
     -v, --version                 same as previous
     -V, --local [pattern]         pretty print all local ciphers (of openssl only). If search pattern supplied: it is an
                                   an ignore case word pattern of cipher hexcode or any other string in its name, kx or bits

"testssl [options] <URI>", where <URI> is:

     <URI>                         host|host:port|URL|URL:port   port 443 is default, URL can only contain HTTPS as a protocol

  and [options] is/are:

     -t, --starttls <protocol>     Does a run against a STARTTLS enabled service which is one of ftp, smtp, lmtp, pop3, imap,
                                   sieve, xmpp, xmpp-server, telnet, ldap, nntp, postgres, mysql
     --xmpphost <to_domain>        For STARTTLS xmpp or xmpp-server checks it supplies the domainname (like SNI)
     --mx <domain/host>            Tests MX records from high to low priority (STARTTLS, port 25)
     --file/-iL <fname>            Mass testing option: Reads one testssl.sh command line per line from <fname>.
                                   Can be combined with --serial or --parallel. Implicitly turns on "--warnings batch".
                                   Text format 1: Comments via # allowed, EOF signals end of <fname>
                                   Text format 2: nmap output in greppable format (-oG), 1 port per line allowed
     --mode <serial|parallel>      Mass testing to be done serial (default) or parallel (--parallel is shortcut for the latter)
     --warnings <batch|off>        "batch" doesn't continue when a testing error is encountered, off continues and skips warnings
     --connect-timeout <seconds>   useful to avoid hangers. Max <seconds> to wait for the TCP socket connect to return
     --openssl-timeout <seconds>   useful to avoid hangers. Max <seconds> to wait before openssl connect will be terminated

single check as <options>  ("testssl URI" does everything except -E and -g):
     -e, --each-cipher             checks each local cipher remotely
     -E, --cipher-per-proto        checks those per protocol
     -s, --std, --categories       tests standard cipher categories by strength
     -f, --fs, --nsa               checks forward secrecy settings
     -p, --protocols               checks TLS/SSL protocols (including SPDY/HTTP2)
     -g, --grease                  tests several server implementation bugs like GREASE and size limitations
     -S, --server-defaults         displays the server's default picks and certificate info
     -P, --server-preference       displays the server's picks: protocol+cipher
     -x, --single-cipher <pattern> tests matched <pattern> of ciphers
                                   (if <pattern> not a number: word match)
     -c, --client-simulation       test client simulations, see which client negotiates with cipher and protocol
     -h, --header, --headers       tests HSTS, HPKP, server/app banner, security headers, cookie, reverse proxy, IPv4 address

     -U, --vulnerable              tests all (of the following) vulnerabilities (if applicable)
     -H, --heartbleed              tests for Heartbleed vulnerability
     -I, --ccs, --ccs-injection    tests for CCS injection vulnerability
     -T, --ticketbleed             tests for Ticketbleed vulnerability in BigIP loadbalancers
     --BB, --robot                 tests for Return of Bleichenbacher's Oracle Threat (ROBOT) vulnerability
     --SI, --starttls-injection    tests for STARTTLS injection issues
     -R, --renegotiation           tests for renegotiation vulnerabilities
     -C, --compression, --crime    tests for CRIME vulnerability (TLS compression issue)
     -B, --breach                  tests for BREACH vulnerability (HTTP compression issue)
     -O, --poodle                  tests for POODLE (SSL) vulnerability
     -Z, --tls-fallback            checks TLS_FALLBACK_SCSV mitigation
     -W, --sweet32                 tests 64 bit block ciphers (3DES, RC2 and IDEA): SWEET32 vulnerability
     -A, --beast                   tests for BEAST vulnerability
     -L, --lucky13                 tests for LUCKY13
     -WS, --winshock               tests for winshock vulnerability
     -F, --freak                   tests for FREAK vulnerability
     -J, --logjam                  tests for LOGJAM vulnerability
     -D, --drown                   tests for DROWN vulnerability
     -4, --rc4, --appelbaum        which RC4 ciphers are being offered?

tuning / connect options (most also can be preset via environment variables):
     -9, --full                    includes tests for implementation bugs and cipher per protocol (could disappear)
     --bugs                        enables the "-bugs" option of s_client, needed e.g. for some buggy F5s
     --assume-http                 if protocol check fails it assumes HTTP protocol and enforces HTTP checks
     --ssl-native                  use OpenSSL where sockets are normally used. Faster but inaccurate, avoid it if possible
     --openssl <PATH>              use this openssl binary (default: look in $PATH, $RUN_DIR of testssl)
     --proxy <host:port|auto>      (experimental) proxy connects via <host:port>, auto: values from $env ($http(s)_proxy)
     -6                            also use IPv6. Works only with supporting OpenSSL version and IPv6 connectivity
     --ip <ip>                     a) tests the supplied <ip> v4 or v6 address instead of resolving host(s) in URI
                                   b) "one" means: just test the first DNS returns (useful for multiple IPs)
                                   c) "proxy" means: dns resolution via proxy. Needed when host has no DNS.
     -n, --nodns <min|none>        if "none": do not try any DNS lookups, "min" queries A, AAAA and MX records
     --sneaky                      leave less traces in target logs: user agent, referer
     --user-agent <user agent>     set a custom user agent instead of the standard user agent
     --ids-friendly                skips a few vulnerability checks which may cause IDSs to block the scanning IP
     --phone-out                   allow to contact external servers for CRL download and querying OCSP responder
     --add-ca <CA files|CA dir>    path to <CAdir> with *.pem or a comma separated list of CA files to include in trust check
     --basicauth <user:pass>       provide HTTP basic auth information.
     --reqheader <header>          add custom http request headers

output options (can also be preset via environment variables):
     --quiet                       don't output the banner. By doing this you acknowledge usage terms normally appearing in the banner
     --wide                        wide output for tests like RC4, BEAST. FS also with hexcode, kx, strength, RFC name
     --show-each                   for wide outputs: display all ciphers tested -- not only succeeded ones
     --mapping <openssl|           openssl: use the OpenSSL cipher suite name as the primary name cipher suite name form (default)
                iana|rfc             -> use the IANA/(RFC) cipher suite name as the primary name cipher suite name form
                no-openssl|          -> don't display the OpenSSL cipher suite name, display IANA/(RFC) names only
                no-iana|no-rfc>      -> don't display the IANA/(RFC) cipher suite name, display OpenSSL names only
     --color <0|1|2|3>             0: no escape or other codes,  1: b/w escape codes,  2: color (default), 3: extra color (color all ciphers)
     --colorblind                  swap green and blue in the output
     --debug <0-6>                 1: screen output normal but keeps debug output in /tmp/.  2-6: see "grep -A 5 '^DEBUG=' testssl.sh"
     --disable-rating              Explicitly disables the rating output

file output options (can also be preset via environment variables)
     --log, --logging              logs stdout to '${NODE}-p${port}${YYYYMMDD-HHMM}.log' in current working directory (cwd)
     --logfile|-oL <logfile>       logs stdout to 'dir/${NODE}-p${port}${YYYYMMDD-HHMM}.log'. If 'logfile' is a dir or to a specified 'logfile'
     --json                        additional output of findings to flat JSON file '${NODE}-p${port}${YYYYMMDD-HHMM}.json' in cwd
     --jsonfile|-oj <jsonfile>     additional output to the specified flat JSON file or directory, similar to --logfile
     --json-pretty                 additional JSON structured output of findings to a file '${NODE}-p${port}${YYYYMMDD-HHMM}.json' in cwd
     --jsonfile-pretty|-oJ <jsonfile>  additional JSON structured output to the specified file or directory, similar to --logfile
     --csv                         additional output of findings to CSV file '${NODE}-p${port}${YYYYMMDD-HHMM}.csv' in cwd or directory
     --csvfile|-oC <csvfile>       additional output as CSV to the specified file or directory, similar to --logfile
     --html                        additional output as HTML to file '${NODE}-p${port}${YYYYMMDD-HHMM}.html'
     --htmlfile|-oH <htmlfile>     additional output as HTML to the specified file or directory, similar to --logfile
     --out(f,F)ile|-oa/-oA <fname> log to a LOG,JSON,CSV,HTML file (see nmap). -oA/-oa: pretty/flat JSON.
                                   "auto" uses '${NODE}-p${port}${YYYYMMDD-HHMM}'. If fname if a dir uses 'dir/${NODE}-p${port}${YYYYMMDD-HHMM}'
     --hints                       additional hints to findings
     --severity <severity>         severities with lower level will be filtered for CSV+JSON, possible values <LOW|MEDIUM|HIGH|CRITICAL>
     --append                      if (non-empty) <logfile>, <csvfile>, <jsonfile> or <htmlfile> exists, append to file. Omits any header
     --overwrite                   if <logfile>, <csvfile>, <jsonfile> or <htmlfile> exists it overwrites it without any warning
     --outprefix <fname_prefix>    before  '${NODE}.' above prepend <fname_prefix>


Options requiring a value can also be called with '=' e.g. testssl.sh -t=smtp --wide --openssl=/usr/bin/openssl <URI>.
<URI> always needs to be the last parameter.
```

## 02 - Usage

`$ testssl <URL>`

- Scan multiple IP addresses

`$ testssl -iL ip_targets.txt`

`$ testssl -U <URL>`

- Gathering subdomains

```
$ testssl --quiet -S -iL ip_targets.txt -oL tls-dns-certificate-output.txt

$ grep -oP '(?!-)[A-Za-z0-9-]{1,63}(?<!-)(\.[A-Za-z0-9-]{2,})+' tls-dns-certificate-output.txt | sort -u > subdomains-output.txt
```

---
## References

- [TestSSL](https://github.com/drwetter/testssl.sh)