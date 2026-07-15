# Manual

## 01 - Common Files

```
/usr/bin/gcc
```

## 02 - Compile After Delivery

^e621f6

```
$ gcc -zexecstack -o payload payload.c && payload & disown
```