# Radare2

### Command Line Arguments

```shell
# run radare2 in debug mode
rizin -d <binary>

# Analyze binary on startup
rizin -A <binary>  # runs aaa
rizin -AA <binary> # runs aaaa

# Run script file - runs commands after loading binary
rizin -i <script> -d <binary>

# Seek to address after file load
rizin -s <addr>
```

### Debugging

```bash
ood <arg1> <arg2>   # restart program in debug mode and send args to current binary
```
