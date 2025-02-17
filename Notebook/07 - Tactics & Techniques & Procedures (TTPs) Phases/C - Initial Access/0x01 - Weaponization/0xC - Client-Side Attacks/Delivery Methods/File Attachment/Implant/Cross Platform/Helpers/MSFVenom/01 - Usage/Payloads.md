# Payloads

To list the payloads options, for example:

```
$ msfvenom -p cmd/unix/reverse_netcat --list-options
```

To list available payloads with a specific platform.

```
$ msfvenom -l payloads --platform <platform>
```

To list available scripting payloads with a specific platform (e.g `unix`).

```
$ msfvenom -l payloads --platform unix | grep "cmd/unix" | awk '{print $1}'
..[omitted]..
```

To list available encoders with a specific platform.

```
$ msfvenom -l encoders --platform <platform>
```

To list available payloads with a specific architecture.

```
$ msfvenom -l payloads -a <architecture>
```

To list available encoders with a specific platform.

```
$ msfvenom -l encoders -a <architecture>
```