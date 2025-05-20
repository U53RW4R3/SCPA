# Detection

Default profile

```
Port - 7443
SSL certificate - Issuer: O=Mythic
```

## Shodan

```
product:"Mythic" port:7443

ssl:"Mythic" port:7443
```

## Censys

```
services.jarm.fingerprint="1dd40d40d00040d00042d43d000000831b6af40378e2dd35eeac4e9311926e" and services.http.response.html_title="Mythic"
```