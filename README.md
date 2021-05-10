# Linux.Nasty
TODO


# Build
Assemble it with [FASM](https://flatassembler.net) x64.
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
TODO

# References:
- TODO
