# Pwntools

## Tips

Run exploit scripts with `PWNLIB_DEBUG=1` for verbose debugging info.

## Processes

## Sockets

## SSH

## Assembly / shellcode

```python
from pwn import *

# Modify execution context
with context.local(encoding="latin", log_level="INFO", arch="amd64"):
    pass # do stuff

# Generate shellcode from assembly
chal_asm = """
start:  cmp     rdi, 0x7f454c46
        mov     eax, 0
        add     eax, [rdi + 4]
        add     eax, [rdi + 8]
        add     eax, [rdi + 12]
"""
shellcode = asm(chal_asm)

### Jumps / relocations
Use `jmp $+0x1338` when doing an indirect jump.
```
