# HTTPx

TODO: Provide more information and probably other use cases

## Setup

```
$ go install github.com/projectdiscovery/httpx/cmd/httpx@latest && \
sudo mv ~/go/bin/httpx /usr/local/bin
```

## Help Menu

```
$ httpx -h
httpx is a fast and multi-purpose HTTP toolkit that allows running multiple probes using the retryablehttp library.

Usage:
  httpx [flags]

Flags:
INPUT:
   -l, -list string      input file containing list of hosts to process
   -rr, -request string  file containing raw request
   -u, -target string[]  input target host(s) to probe

PROBES:
   -sc, -status-code     display response status-code
   -cl, -content-length  display response content-length
   -ct, -content-type    display response content-type
   -location             display response redirect location
   -favicon              display mmh3 hash for '/favicon.ico' file
   -hash string          display response body hash (supported: md5,mmh3,simhash,sha1,sha256,sha512)
   -jarm                 display jarm fingerprint hash
   -rt, -response-time   display response time
   -lc, -line-count      display response body line count
   -wc, -word-count      display response body word count
   -title                display page title
   -server, -web-server  display server name
   -td, -tech-detect     display technology in use based on wappalyzer dataset
   -method               display http request method
   -websocket            display server using websocket
   -ip                   display host ip
   -cname                display host cname
   -asn                  display host asn information
   -cdn                  display cdn in use
   -probe                display probe status

HEADLESS:
   -ss, -screenshot  enable saving screenshot of the page using headless browser
   -system-chrome    enable using local installed chrome for screenshot

MATCHERS:
   -mc, -match-code string            match response with specified status code (-mc 200,302)
   -ml, -match-length string          match response with specified content length (-ml 100,102)
   -mlc, -match-line-count string     match response body with specified line count (-mlc 423,532)
   -mwc, -match-word-count string     match response body with specified word count (-mwc 43,55)
   -mfc, -match-favicon string[]      match response with specified favicon hash (-mfc 1494302000)
   -ms, -match-string string          match response with specified string (-ms admin)
   -mr, -match-regex string           match response with specified regex (-mr admin)
   -mcdn, -match-cdn string[]         match host with specified cdn provider (fastly, google, leaseweb, stackpath, cloudfront)
   -mrt, -match-response-time string  match response with specified response time in seconds (-mrt '< 1')
   -mdc, -match-condition string      match response with dsl expression condition

EXTRACTOR:
   -er, -extract-regex string[]   display response content with matched regex
   -ep, -extract-preset string[]  display response content matched by a pre-defined regex (mail,url,ipv4)

FILTERS:
   -fc, -filter-code string            filter response with specified status code (-fc 403,401)
   -fep, -filter-error-page            filter response with ML based error page detection
   -fl, -filter-length string          filter response with specified content length (-fl 23,33)
   -flc, -filter-line-count string     filter response body with specified line count (-flc 423,532)
   -fwc, -filter-word-count string     filter response body with specified word count (-fwc 423,532)
   -ffc, -filter-favicon string[]      filter response with specified favicon hash (-mfc 1494302000)
   -fs, -filter-string string          filter response with specified string (-fs admin)
   -fe, -filter-regex string           filter response with specified regex (-fe admin)
   -fcdn, -filter-cdn string[]         filter host with specified cdn provider (fastly, google, leaseweb, stackpath, cloudfront)
   -frt, -filter-response-time string  filter response with specified response time in seconds (-frt '> 1')
   -fdc, -filter-condition string      filter response with dsl expression condition

RATE-LIMIT:
   -t, -threads int              number of threads to use (default 50)
   -rl, -rate-limit int          maximum requests to send per second (default 150)
   -rlm, -rate-limit-minute int  maximum number of requests to send per minute

MISCELLANEOUS:
   -pa, -probe-all-ips        probe all the ips associated with same host
   -p, -ports string[]        ports to probe (nmap syntax: eg http:1,2-10,11,https:80)
   -path string               path or list of paths to probe (comma-separated, file)
   -tls-probe                 send http probes on the extracted TLS domains (dns_name)
   -csp-probe                 send http probes on the extracted CSP domains
   -tls-grab                  perform TLS(SSL) data grabbing
   -pipeline                  probe and display server supporting HTTP1.1 pipeline
   -http2                     probe and display server supporting HTTP2
   -vhost                     probe and display server supporting VHOST
   -ldv, -list-dsl-variables  list json output field keys name that support dsl matcher/filter

UPDATE:
   -up, -update                 update httpx to latest version
   -duc, -disable-update-check  disable automatic httpx update check

OUTPUT:
   -o, -output string                  file to write output results
   -oa, -output-all                    filename to write output results in all formats
   -sr, -store-response                store http response to output directory
   -srd, -store-response-dir string    store http response to custom directory
   -csv                                store output in csv format
   -csvo, -csv-output-encoding string  define output encoding
   -json                               store output in JSONL(ines) format
   -irr, -include-response             include http request/response in JSON output (-json only)
   -irrb, -include-response-base64     include base64 encoded http request/response in JSON output (-json only)
   -include-chain                      include redirect http chain in JSON output (-json only)
   -store-chain                        include http redirect chain in responses (-sr only)

CONFIGURATIONS:
   -config string                path to the httpx configuration file (default $HOME/.config/httpx/config.yaml)
   -r, -resolvers string[]       list of custom resolver (file or comma separated)
   -allow string[]               allowed list of IP/CIDR's to process (file or comma separated)
   -deny string[]                denied list of IP/CIDR's to process (file or comma separated)
   -sni, -sni-name string        custom TLS SNI name
   -random-agent                 enable Random User-Agent to use (default true)
   -H, -header string[]          custom http headers to send with request
   -http-proxy, -proxy string    http proxy to use (eg http://127.0.0.1:8080)
   -unsafe                       send raw requests skipping golang normalization
   -resume                       resume scan using resume.cfg
   -fr, -follow-redirects        follow http redirects
   -maxr, -max-redirects int     max number of redirects to follow per host (default 10)
   -fhr, -follow-host-redirects  follow redirects on the same host
   -vhost-input                  get a list of vhosts as input
   -x string                     request methods to probe, use 'all' to probe all HTTP methods
   -body string                  post body to include in http request
   -s, -stream                   stream mode - start elaborating input targets without sorting
   -sd, -skip-dedupe             disable dedupe input items (only used with stream mode)
   -ldp, -leave-default-ports    leave default http/https ports in host header (eg. http://host:80 - https://host:443
   -ztls                         use ztls library with autofallback to standard one for tls13
   -no-decode                    avoid decoding body
   -tlsi, -tls-impersonate       enable experimental client hello (ja3) tls randomization
   -no-stdin                     Disable Stdin processing

DEBUG:
   -health-check, -hc        run diagnostic check up
   -debug                    display request/response content in cli
   -debug-req                display request content in cli
   -debug-resp               display response content in cli
   -version                  display httpx version
   -stats                    display scan statistic
   -profile-mem string       optional httpx memory profile dump file
   -silent                   silent mode
   -v, -verbose              verbose mode
   -si, -stats-interval int  number of seconds to wait between showing a statistics update (default: 5)
   -nc, -no-color            disable colors in cli output

OPTIMIZATIONS:
   -nf, -no-fallback                  display both probed protocol (HTTPS and HTTP)
   -nfs, -no-fallback-scheme          probe with protocol scheme specified in input 
   -maxhr, -max-host-error int        max error count per host before skipping remaining path/s (default 30)
   -ec, -exclude-cdn                  skip full port scans for CDNs (only checks for 80,443)
   -retries int                       number of retries
   -timeout int                       timeout in seconds (default 10)
   -delay value                       duration between each http request (eg: 200ms, 1s) (default -1ns)
   -rsts, -response-size-to-save int  max response size to save in bytes (default 2147483647)
   -rstr, -response-size-to-read int  max response size to read in bytes (default 2147483647)
```

## Usage

```
$ httpx -u <URL> -o live-url-output.txt
```

```
$ httpx -l urls.txt -o live-urls-output.txt
```

```
$ httpx -l urls.txt -probe -o live-urls-output.txt
```

```
$ httpx -l urls.txt -ip -o live-urls-ips-output.txt
```

```
$ httpx -l urls.txt -fr -o live-urls-output.txt
```

```
$ httpx -l urls.txt -mc 200,204,301,302,307,308,404,410,500,520,526 -o live-urls-output.txt
```

```
$ httpx -l urls.txt -fc 401,403,408,409,502 -o live-urls-output.txt
```

```
$ httpx -l urls.txt -probe -sc -title -server -td -o live-urls-output.txt
```

```
$ httpx -l urls.txt -p 80,443,900,3000,5000,7070,8000,8008,8080,8443,9000,9200,15672
```

## Use Cases

TODO: Provide more use cases when using httpx

### Retrieve Active URLs

```
$ subfinder -dL domains.txt | dnsx -silent | httpx -mc 200,204,301,302,307,308,404,410,500,520,526 -o active-urls-output.txt
```

### Webmails

Outlook

```
$ httpx -silent -l urls.txt -s -sd -location | awk '/owa/ {print substr($1,9) }' > outlook-web-application-output.txt
```

### Gather Endpoints

```
$ subfinder -dL domains.txt | dnsx | waybackurl | uro | grep -Po "https?://[a-zA-Z0-9./?=_-]*(:[[:digit:]]+)?(?:\?|\&)(?<key>[\w]+)(?:\=|\&?)(?<value>[\w+,.-]*)" | httpx -silent -o active-url-endpoints.txt
```

---
## References

### Github

- [HTTPx](https://github.com/projectdiscovery/httpx)

### Mozilla

- [Mozilla: HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

### Hacking Articles

- [Hacking Articles: A detailed Guide on HTTPx](https://www.hackingarticles.in/a-detailed-guide-on-httpx/)

### Enlace Hacktivista

- [Enlace Hacktivista: Initial Access Tactics, techniques and procedures](https://enlacehacktivista.org/index.php?title=Initial_Access_Tactics,_techniques_and_procedures)