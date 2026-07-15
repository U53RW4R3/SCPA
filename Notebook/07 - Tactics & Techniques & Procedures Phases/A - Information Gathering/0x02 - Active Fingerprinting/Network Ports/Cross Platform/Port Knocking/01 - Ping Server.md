# 01 - Ping Server

> [!INFO] Pay Attention User!
> Lookout for `Destination Port Unreachable` with keyword **`Port`**. It's different from `Destination Host Unreachable`.

## Manual

```
$ ping -c 3 <IP>
```

## #hping3

```
# hping3 -c 4 -1 <IP>
```