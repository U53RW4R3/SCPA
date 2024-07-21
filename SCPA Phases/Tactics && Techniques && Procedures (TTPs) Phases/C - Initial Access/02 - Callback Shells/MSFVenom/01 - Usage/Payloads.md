# Payloads

To list the payloads options, for example:

```
$ msfvenom -p cmd/unix/reverse_netcat --list-options
```

To list scripting payloads.

```
$ msfvenom -l payloads | grep "cmd/unix" | awk '{print $1}'
..[truncated]..
```

To list payloads with a specific platform.

```
$ msfvenom -l payloads --platform <platform>
```

To list encoders with a specific platform.

```
$ msfvenom -l encoders --platform <platform>
```

To list payloads with a specific architecture.

```
$ msfvenom -l payloads -a <architecture>
```

To list encoders with a specific platform.

```
$ msfvenom -l encoders -a <architecture>
```