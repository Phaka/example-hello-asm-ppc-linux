# Hello World in PowerPC Assembly (Linux)

A simple Hello World implementation in 32-bit PowerPC assembly language for Linux systems. This implementation is for traditional big-endian PowerPC systems, common in older embedded systems and classic PowerPC workstations.

## Installation

On a PowerPC Linux system, you'll need the standard GNU toolchain:

```bash
sudo apt-get update
sudo apt-get install binutils gcc
```

## Running

Assemble and link:
```bash
as -o main.o main.s -mbig -32
ld -o hello main.o
./hello
```

## Code Explanation

The 32-bit PowerPC implementation shows several differences from its 64-bit counterpart. The architecture uses simpler addressing modes and requires less complex address loading sequences.

Key architectural features:

Memory Access:
- Uses big-endian byte ordering
- 32-bit address space simplifies address loading
- Alignment follows 32-bit (4-byte) boundaries
- Uses @ha and @l for address calculations instead of the more complex 64-bit addressing

Register Usage:
- Register 0: System call number
- Register 3: First argument (file descriptor or return code)
- Register 4: Second argument (message address)
- Register 5: Third argument (message length)

Instructions:
- li (Load Immediate): Loads a 16-bit value
- lis (Load Immediate Shifted): Loads a 16-bit value into the upper half
- la (Load Address): Combines base and displacement
- sc (System Call): Triggers kernel service

The 32-bit implementation is simpler than the 64-bit version because:
- Addresses are 32 bits instead of 64 bits
- Fewer instructions needed for address loading
- Memory alignment requirements are less strict
- No need for complex address construction sequences
