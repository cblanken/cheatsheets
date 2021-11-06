# Volatility3 Cheatsheet

## Windows
### Process Info
```bash
vol.py -f memdump.mem windows.info.Info
```
### Process Dump
```bash
vol.py -f memdump.mem windows.pslist.PsList
vol.py -f memdump.mem windows.pstree.PsTree
```

### Memory Dump

### DLLs
```bash
vol.py -f memdump.mem windows.dlllist.DllList
vol.py -f memdump.mem windows.dumpfiles.DumpFiles --pid <pid>
```

### Network Info
```bash
vol.py -f memdump.mem windows.netscan.NetScan
```

### Registry

### Malware
```bash
vol.py -f memdump.mem windows.malfind.Malfind --dump
```
