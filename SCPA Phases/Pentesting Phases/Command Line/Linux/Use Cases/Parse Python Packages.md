# Parse Python Packages

```
$ packages=$(awk -F "=" '{print "python3-"$1}' requirements.txt | tr "\n" " ")

$ sudo apt install -y $packages
```