# GDB

Brackets `[` `]` may be used inside command sequences to indicate potential shortcuts.

## Help

Use `apro[pos] [REGEX]` to search the gdb help menus

## Debugging

### Break / Breakpoints

Show breakpoints with `info br[eakpoints]`
Set a conditional breakpoint with `break [address] if [condition]`
Delete breakpoints with `delete br[eakpoints]`

- Watchpoints
- Catchpoints
- Tracepoints

### Stepping / Seeking

## Layout

Use `tui dis[able]` or the shortcut `ctrl + x` `a` to close any TUI layout.

## Memory

Searching

Examining

Printing

## Variables

- Print local variables with `info locals`.
- Print all static and globals with `info var[iables]`.
    - This command may also take a regex parameter like `info variables [REGEX]`
    - The regex can apply to the variable type with `-t` like `info variables -t uint`
- Set a variable with `set $[VARIABLE] = [VALUE]`
- Print a variable with `p[rint] $[VARIABLE]`

## Threads

Print the backtrace for all threads with `thread apply all bt`

## Artificial Arrays

## Tips and Tricks

- Use `pipe [command] | [shell_command]` to send gdb command output to a shell
command
- Position-Independent Executable can be a pain to debug. `gdb` loads them at either `0x000055555555554000` or `0x7ffff7ffc000`. To make it easier to add breakpoints you can set a `$base` address in your gdb script like this `set $base =00x7ffff7ffc000` and then set breakpoints with `break *($base +00x1023)` for example.

## Pwndbg

The pwndbg extension features.



