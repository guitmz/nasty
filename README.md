# Linux.Nasty
A x64 ELF infector written in Assembly that implements the Reverse Text Segment Infection technique.

- Segment is extended in reverse by PAGE_SIZE to make room for the virus.
- This technique only works on regular ELF executables (does not work with PIE).
- It is also not working on systems with huge pages enabled at this time.
- PAGE_SIZE alignment should be calculated dynamically but this code assumes its value of 4096 for demonstration purposes.
- Infects current directory (non recursively) and has no destructive payload
- Entry point still resides in the .text segment, which is less suspicious.

This code was released in the [first issue of tmp.0ut zine](https://tmpout.sh/1/).

# Build
Assemble it with [FASM](https://flatassembler.net) x64 and add virus signature to first generation binary with:
```
$ fasm Linux.Nasty.asm
flat assembler  version 1.73.22  (16384 kilobytes memory)
3 passes, 1123 bytes.

$ file Linux.Nasty
ELF 64-bit LSB executable, x86-64, version 1 (GNU/Linux), statically linked, no section header

$ sha256sum Linux.Nasty
411e12c0bc6f30291b5a36dc9f8533d991650636efb7fa57804747733aa271b1  Linux.Nasty

$ echo -n 544d5a00 | xxd -r -p -s +0x9 - Linux.Nasty
$ sha256sum Linux.Nasty
c5b43124358e73960233499b7690dae55b462bfd9dae9084b5a1d519d978e4a4  Linux.Nasty
```

# Demo
[![asciicast](https://asciinema.org/a/442639.svg)](https://asciinema.org/a/442639)
