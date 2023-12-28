# Checklist

Search Tag(s): #checklist #server-side-template-injection #webapp

TODO: Provide more list for the SSTI checklist

## Vulnerability Assessment

### Scanners

#### General

- [ ] You can use XSS scanners to perform and inject Cross-Site Scripting (XSS) payloads for heuristic checks as a probable indicator for SSTI exploits.
	- [[Dalfox]]
- [ ] Using [[Webapps|Nuclei]] with fuzzer templates to discover GET request URLs with SSTI vulnerabilities.

- [ ] Try to inject XSS payloads and then perform the mathematical expressions 
- [ ] Check Cookie headers to inject
- [ ] Inject X-Forwarded-For