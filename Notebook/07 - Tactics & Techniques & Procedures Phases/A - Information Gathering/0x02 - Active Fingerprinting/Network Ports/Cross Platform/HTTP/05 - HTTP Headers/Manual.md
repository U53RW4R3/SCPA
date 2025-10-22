# Manual

## 01 - `wget`

```
$ wget -qS --spider [--no-check-certificate] <URL>
```

## 02 - cURL

```
$ curl [-k] <URL>
```

## 03 - `httpie`

```
$ http -F --headers <URL>
```

Output only the response headers.

```
$ http [-F] -p h <URL>
```

Output only the request headers.

```
$ http -F -p H <URL>
```