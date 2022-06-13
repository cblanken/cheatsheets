# C Cheatsheet

## Syntax
```c
// Printing
// Printing to STDOUT
#include <stdio.h>
#include <stdlib.h>
int main(void) {
    if(puts("Hello, world!") == EOF) {
        return EXIT_FAILURE;
    }
    return EXIT_SUCCESS;
}

// Formatted output
printf("%s\n", "Hello, world!");

// Operators
// Increment and Decrement Operators "++" and "--"
int e, i = 5;
e = i++; // postfix increment: i has the value 6; e has the value 5
e = i--; // postfix decrement: i has the value 5; e has the value 6
e = ++i; // prefix increment: i has the value 6; e has the value 6
e = --i; // prefix decrement: i has the value 5; e has the value 5
```

## Files / IO

## Sockets / Networking

## Build Tools
- [make](https://www.gnu.org/software/make/)
- [CMake](https://cmake.org/)

## Testing Frameworks
- [tau](https://github.com/jasmcaus/tau)
- [Check](https://libcheck.github.io/check/)
