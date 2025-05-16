# Volatility3

## Windows

### Process Info

```shell
vol.py -f memdump.mem windows.info.Info
```

### Process Dump

```shell
vol.py -f memdump.mem windows.pslist.PsList
vol.py -f memdump.mem windows.pstree.PsTree
```

### Memory Dump

### DLLs

```shell
vol.py -f memdump.mem windows.dlllist.DllList
vol.py -f memdump.mem windows.dumpfiles.DumpFiles --pid <pid>
```

### Network Info

```shell
vol.py -f memdump.mem windows.netscan.NetScan
```

### Registry

### Malware

```shell
vol.py -f memdump.mem windows.malfind.Malfind --dump
```
