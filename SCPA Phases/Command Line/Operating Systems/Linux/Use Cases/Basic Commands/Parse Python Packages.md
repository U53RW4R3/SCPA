# Parse Python Packages

Search Tag(s): #command-line #use-cases #linux

```
$ packages=$(awk -F "=" '{print "python3-"$1}' requirements.txt | tr "\n" " ")

$ sudo apt install -y $packages
```