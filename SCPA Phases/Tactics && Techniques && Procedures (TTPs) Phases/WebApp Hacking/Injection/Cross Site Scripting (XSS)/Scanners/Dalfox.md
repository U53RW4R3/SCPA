# Dalfox

Search Tag(s): #xss #webapp

## Setup

```
$ go install github.com/hahwul/dalfox/v2@latest && \
sudo cp ~/go/bin/dalfox /usr/local/bin
```

## Help Menu

```
$ dalfox -h
Usage:
  dalfox [flags]
  dalfox [command]

Available Commands:
  completion  Generate the autocompletion script for the specified shell
  file        Use file mode(targets list or rawdata)
  help        Help about any command
  payload     Payload mode, make and enum payloads
  pipe        Use pipeline mode
  server      Start API Server
  sxss        Use Stored XSS mode
  url         Use single target mode
  version     Show version

Flags:
  -b, --blind string                Add your blind xss
                                      * Example: -b your-callback-url
      --config string               Using config from file
  -C, --cookie string               Add custom cookie
      --cookie-from-raw string      Load cookie from burp raw http request
                                      * Example: --cookie-from-raw request.txt
      --custom-alert-type string    Change alert value type
                                      * Example: --custom-alert-type=none / --custom-alert-type=str,none (default "none")
      --custom-alert-value string   Change alert value
                                      * Example: --custom-alert-value=document.cookie (default "1")
      --custom-payload string       Add custom payloads from file
  -d, --data string                 Using POST Method and add Body data
      --debug                       debug mode, save all log using -o option
      --deep-domxss                 DOM XSS Testing with more payloads on headless [so slow]
      --delay int                   Milliseconds between send to same host (1000==1s)
  -F, --follow-redirects            Following redirection
      --format string               Stdout output format
                                      * Supported: plain / json (default "plain")
      --found-action string         If found weak/vuln, action(cmd) to next
                                      * Example: --found-action='./notify.sh'
      --found-action-shell string   Select shell application for --found-action (default "bash")
      --grep string                 Using custom grepping file
                                      * Example: --grep ./samples/sample_grep.json
      --har-file-path string        Path to save HAR of scan requests to
  -H, --header strings              Add custom headers
  -h, --help                        help for dalfox
      --ignore-param strings        Ignores this parameter when scanning.
                                      * Example: --ignore-param api_token --ignore-param csrf_token
      --ignore-return string        Ignores scanning from return code
                                      * Example: --ignore-return 302,403,404
  -X, --method string               Force overriding HTTP Method
                                      * Example: -X PUT (default "GET")
      --mining-dict                 Find new parameter with dictionary attack, default is Gf-Patterns=>XSS (default true)
  -W, --mining-dict-word string     Custom wordlist file for param mining
                                      * Example: --mining-dict-word word.txt
      --mining-dom                  Find new parameter in DOM (attribute/js value) (default true)
      --no-color                    Not use colorize
      --no-spinner                  Not use spinner
      --only-custom-payload         Only testing custom payload (required --custom-payload)
      --only-discovery              Only testing parameter analysis (same '--skip-xss-scanning' option)
      --only-poc string             Shows only the PoC code for the specified pattern (g: grep / r: reflected / v: verified)
                                     * Example: --only-poc='g,v'
  -o, --output string               Write to output file (By default, only the PoC code is saved)
      --output-all                  All log write mode (-o or stdout)
      --output-request              Include raw HTTP requests in the results.
      --output-response             Include raw HTTP response in the results.
  -p, --param strings               Only testing selected parameters
      --poc-type string             Select PoC type 
                                     * Supported: plain/curl/httpie/http-request
                                     * Example: --poc-type='curl' (default "plain")
      --proxy string                Send all request to proxy server
                                      * Example: --proxy http://127.0.0.1:8080
      --remote-payloads string      Using remote payload for XSS testing
                                      * Supported: portswigger/payloadbox
                                      * Example: --remote-payloads=portswigger,payloadbox
      --remote-wordlists string     Using remote wordlists for param mining
                                      * Supported: burp/assetnote
                                      * Example: --remote-wordlists=burp
      --report                      Show detail report
      --report-format string        Format of --report flag [plain/json] (default "plain")
  -S, --silence                     Only print PoC Code and Progress(for pipe/file mode)
      --skip-bav                    Skipping BAV(Basic Another Vulnerability) analysis
      --skip-grepping               Skipping built-in grepping
      --skip-headless               Skipping headless browser base scanning[DOM XSS and inJS verify]
      --skip-mining-all             Skipping ALL parameter mining
      --skip-mining-dict            Skipping Dict base parameter mining
      --skip-mining-dom             Skipping DOM base parameter mining
      --skip-xss-scanning           Skipping XSS Scanning (same '--only-discovery' option)
      --timeout int                 Second of timeout (default 10)
      --user-agent string           Add custom UserAgent
      --waf-evasion                 Avoid blocking by adjusting the speed when detecting WAF (worker=1 delay=3s)
  -w, --worker int                  Number of worker (default 100)

Use "dalfox [command] --help" for more information about a command.
```

## Usage

TODO: Fill this info

`$ dalfox url http[s]://<IP>/ | cut -d " " -f 2 > xss_vulns.txt`

`$ dalfox file urls.txt | cut -d " " -f 2 > xss_vulns.txt`

## Use Cases

### Gathering Endpoints

`$ gospider -S urls.txt -c 10 -d 5 --blacklist ".(jpg|jpeg|gif|css|tif|tiff|png|ttf|woff|woff2|ico|pdf|svg|txt)" --other-source | grep -e code-200 | grep -Po "https?://[a-zA-Z0-9./?=_-]*(:[[:digit:]]+)?(?:\?|\&)(?<key>[\w]+)(?:\=|\&?)(?<value>[\w+,.-]*)" | qsreplace -a | dalfox pipe -o xss-endpoints-vulns.txt`

---
## References

- [Dalfox](https://github.com/hahwul/dalfox)

- [Dalfox Documentation](https://dalfox.hahwul.com/docs/home/)