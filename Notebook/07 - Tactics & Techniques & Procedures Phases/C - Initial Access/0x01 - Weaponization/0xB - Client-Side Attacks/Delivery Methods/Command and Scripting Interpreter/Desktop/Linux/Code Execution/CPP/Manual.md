# Manual

## 01 - Common Files

```
/usr/bin/g++
```

## 02 - Compile After Delivery

^e01813

```
$ g++ [-zexecstack] -o payload payload.cpp && payload & disown
```