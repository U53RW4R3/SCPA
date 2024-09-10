# Manual

## 01 - `wget`

```
$ wget -q --no-check-certificate --spider -S <URL>
```

## 02 - cURL

```
$ curl -k <URL>
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