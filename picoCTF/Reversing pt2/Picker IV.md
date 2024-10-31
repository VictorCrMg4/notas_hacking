
## Objetivo
Can you figure out how this program works to get the flag? Connect to the program with netcat: `$ nc saturn.picoctf.net 60687` The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/528/picker-IV.c). The binary can be downloaded [here](https://artifacts.picoctf.net/c/528/picker-IV).
## Solución
Buscamos el apuntado de la funcion win
```bash
┌──(kali㉿kali)-[~/picoCTF/reversing2]
└─$ readelf -a picker-IV 
ELF Header:
  Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF64
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           Advanced Micro Devices X86-64
  Version:                           0x1
  Entry point address:               0x401190
  Start of program headers:          64 (bytes into file)
  Start of section headers:          15288 (bytes into file)
  Flags:                             0x0
  Size of this header:               64 (bytes)
  Size of program headers:           56 (bytes)
  Number of program headers:         13
  Size of section headers:           64 (bytes)
  Number of section headers:         31
  Section header string table index: 30

Section Headers:
  [Nr] Name              Type             Address           Offset
       Size              EntSize          Flags  Link  Info  Align
  [ 0]                   NULL             0000000000000000  00000000
       0000000000000000  0000000000000000           0     0     0
  [ 1] .interp           PROGBITS         0000000000400318  00000318
       000000000000001c  0000000000000000   A       0     0     1
  [ 2] .note.gnu.pr[...] NOTE             0000000000400338  00000338
       0000000000000020  0000000000000000   A       0     0     8
  [ 3] .note.gnu.bu[...] NOTE             0000000000400358  00000358
       0000000000000024  0000000000000000   A       0     0     4
  [ 4] .note.ABI-tag     NOTE             000000000040037c  0000037c
       0000000000000020  0000000000000000   A       0     0     4
  [ 5] .gnu.hash         GNU_HASH         00000000004003a0  000003a0
       0000000000000024  0000000000000000   A       6     0     8
  [ 6] .dynsym           DYNSYM           00000000004003c8  000003c8
       0000000000000168  0000000000000018   A       7     1     8
  [ 7] .dynstr           STRTAB           0000000000400530  00000530
       0000000000000099  0000000000000000   A       0     0     1
  [ 8] .gnu.version      VERSYM           00000000004005ca  000005ca
       000000000000001e  0000000000000002   A       6     0     2
  [ 9] .gnu.version_r    VERNEED          00000000004005e8  000005e8
       0000000000000030  0000000000000000   A       7     1     8
  [10] .rela.dyn         RELA             0000000000400618  00000618
       0000000000000048  0000000000000018   A       6     0     8
  [11] .rela.plt         RELA             0000000000400660  00000660
       0000000000000108  0000000000000018  AI       6    24     8
  [12] .init             PROGBITS         0000000000401000  00001000
       000000000000001b  0000000000000000  AX       0     0     4
  [13] .plt              PROGBITS         0000000000401020  00001020
       00000000000000c0  0000000000000010  AX       0     0     16
  [14] .plt.sec          PROGBITS         00000000004010e0  000010e0
       00000000000000b0  0000000000000010  AX       0     0     16
  [15] .text             PROGBITS         0000000000401190  00001190
       00000000000002b5  0000000000000000  AX       0     0     16
  [16] .fini             PROGBITS         0000000000401448  00001448
       000000000000000d  0000000000000000  AX       0     0     4
  [17] .rodata           PROGBITS         0000000000402000  00002000
       0000000000000099  0000000000000000   A       0     0     8
  [18] .eh_frame_hdr     PROGBITS         000000000040209c  0000209c
       0000000000000054  0000000000000000   A       0     0     4
  [19] .eh_frame         PROGBITS         00000000004020f0  000020f0
       0000000000000140  0000000000000000   A       0     0     8
  [20] .init_array       INIT_ARRAY       0000000000403e10  00002e10
       0000000000000008  0000000000000008  WA       0     0     8
  [21] .fini_array       FINI_ARRAY       0000000000403e18  00002e18
       0000000000000008  0000000000000008  WA       0     0     8
  [22] .dynamic          DYNAMIC          0000000000403e20  00002e20
       00000000000001d0  0000000000000010  WA       7     0     8
  [23] .got              PROGBITS         0000000000403ff0  00002ff0
       0000000000000010  0000000000000008  WA       0     0     8
  [24] .got.plt          PROGBITS         0000000000404000  00003000
       0000000000000070  0000000000000008  WA       0     0     8
  [25] .data             PROGBITS         0000000000404070  00003070
       0000000000000010  0000000000000000  WA       0     0     8
  [26] .bss              NOBITS           0000000000404080  00003080
       0000000000000010  0000000000000000  WA       0     0     8
  [27] .comment          PROGBITS         0000000000000000  00003080
       000000000000002b  0000000000000001  MS       0     0     1
  [28] .symtab           SYMTAB           0000000000000000  000030b0
       0000000000000720  0000000000000018          29    45     8
  [29] .strtab           STRTAB           0000000000000000  000037d0
       00000000000002c3  0000000000000000           0     0     1
  [30] .shstrtab         STRTAB           0000000000000000  00003a93
       000000000000011f  0000000000000000           0     0     1
Key to Flags:
  W (write), A (alloc), X (execute), M (merge), S (strings), I (info),
  L (link order), O (extra OS processing required), G (group), T (TLS),
  C (compressed), x (unknown), o (OS specific), E (exclude),
  D (mbind), l (large), p (processor specific)

There are no section groups in this file.

Program Headers:
  Type           Offset             VirtAddr           PhysAddr
                 FileSiz            MemSiz              Flags  Align
  PHDR           0x0000000000000040 0x0000000000400040 0x0000000000400040
                 0x00000000000002d8 0x00000000000002d8  R      0x8
  INTERP         0x0000000000000318 0x0000000000400318 0x0000000000400318
                 0x000000000000001c 0x000000000000001c  R      0x1
      [Requesting program interpreter: /lib64/ld-linux-x86-64.so.2]
  LOAD           0x0000000000000000 0x0000000000400000 0x0000000000400000
                 0x0000000000000768 0x0000000000000768  R      0x1000
  LOAD           0x0000000000001000 0x0000000000401000 0x0000000000401000
                 0x0000000000000455 0x0000000000000455  R E    0x1000
  LOAD           0x0000000000002000 0x0000000000402000 0x0000000000402000
                 0x0000000000000230 0x0000000000000230  R      0x1000
  LOAD           0x0000000000002e10 0x0000000000403e10 0x0000000000403e10
                 0x0000000000000270 0x0000000000000280  RW     0x1000
  DYNAMIC        0x0000000000002e20 0x0000000000403e20 0x0000000000403e20
                 0x00000000000001d0 0x00000000000001d0  RW     0x8
  NOTE           0x0000000000000338 0x0000000000400338 0x0000000000400338
                 0x0000000000000020 0x0000000000000020  R      0x8
  NOTE           0x0000000000000358 0x0000000000400358 0x0000000000400358
                 0x0000000000000044 0x0000000000000044  R      0x4
  GNU_PROPERTY   0x0000000000000338 0x0000000000400338 0x0000000000400338
                 0x0000000000000020 0x0000000000000020  R      0x8
  GNU_EH_FRAME   0x000000000000209c 0x000000000040209c 0x000000000040209c
                 0x0000000000000054 0x0000000000000054  R      0x4
  GNU_STACK      0x0000000000000000 0x0000000000000000 0x0000000000000000
                 0x0000000000000000 0x0000000000000000  RW     0x10
  GNU_RELRO      0x0000000000002e10 0x0000000000403e10 0x0000000000403e10
                 0x00000000000001f0 0x00000000000001f0  R      0x1

 Section to Segment mapping:
  Segment Sections...
   00     
   01     .interp 
   02     .interp .note.gnu.property .note.gnu.build-id .note.ABI-tag .gnu.hash .dynsym .dynstr .gnu.version .gnu.version_r .rela.dyn .rela.plt 
   03     .init .plt .plt.sec .text .fini 
   04     .rodata .eh_frame_hdr .eh_frame 
   05     .init_array .fini_array .dynamic .got .got.plt .data .bss 
   06     .dynamic 
   07     .note.gnu.property 
   08     .note.gnu.build-id .note.ABI-tag 
   09     .note.gnu.property 
   10     .eh_frame_hdr 
   11     
   12     .init_array .fini_array .dynamic .got 

Dynamic section at offset 0x2e20 contains 24 entries:
  Tag        Type                         Name/Value
 0x0000000000000001 (NEEDED)             Shared library: [libc.so.6]
 0x000000000000000c (INIT)               0x401000
 0x000000000000000d (FINI)               0x401448
 0x0000000000000019 (INIT_ARRAY)         0x403e10
 0x000000000000001b (INIT_ARRAYSZ)       8 (bytes)
 0x000000000000001a (FINI_ARRAY)         0x403e18
 0x000000000000001c (FINI_ARRAYSZ)       8 (bytes)
 0x000000006ffffef5 (GNU_HASH)           0x4003a0
 0x0000000000000005 (STRTAB)             0x400530
 0x0000000000000006 (SYMTAB)             0x4003c8
 0x000000000000000a (STRSZ)              153 (bytes)
 0x000000000000000b (SYMENT)             24 (bytes)
 0x0000000000000015 (DEBUG)              0x0
 0x0000000000000003 (PLTGOT)             0x404000
 0x0000000000000002 (PLTRELSZ)           264 (bytes)
 0x0000000000000014 (PLTREL)             RELA
 0x0000000000000017 (JMPREL)             0x400660
 0x0000000000000007 (RELA)               0x400618
 0x0000000000000008 (RELASZ)             72 (bytes)
 0x0000000000000009 (RELAENT)            24 (bytes)
 0x000000006ffffffe (VERNEED)            0x4005e8
 0x000000006fffffff (VERNEEDNUM)         1
 0x000000006ffffff0 (VERSYM)             0x4005ca
 0x0000000000000000 (NULL)               0x0

Relocation section '.rela.dyn' at offset 0x618 contains 3 entries:
  Offset          Info           Type           Sym. Value    Sym. Name + Addend
000000403ff0  000600000006 R_X86_64_GLOB_DAT 0000000000000000 __libc_start_main@GLIBC_2.2.5 + 0
000000403ff8  000800000006 R_X86_64_GLOB_DAT 0000000000000000 __gmon_start__ + 0
000000404080  000e00000005 R_X86_64_COPY     0000000000404080 stdout@GLIBC_2.2.5 + 0

Relocation section '.rela.plt' at offset 0x660 contains 11 entries:
  Offset          Info           Type           Sym. Value    Sym. Name + Addend
000000404018  000100000007 R_X86_64_JUMP_SLO 0000000000000000 putchar@GLIBC_2.2.5 + 0
000000404020  000200000007 R_X86_64_JUMP_SLO 0000000000000000 puts@GLIBC_2.2.5 + 0
000000404028  000300000007 R_X86_64_JUMP_SLO 0000000000000000 fclose@GLIBC_2.2.5 + 0
000000404030  000400000007 R_X86_64_JUMP_SLO 0000000000000000 printf@GLIBC_2.2.5 + 0
000000404038  000500000007 R_X86_64_JUMP_SLO 0000000000000000 fgetc@GLIBC_2.2.5 + 0
000000404040  000700000007 R_X86_64_JUMP_SLO 0000000000000000 signal@GLIBC_2.2.5 + 0
000000404048  000900000007 R_X86_64_JUMP_SLO 0000000000000000 setvbuf@GLIBC_2.2.5 + 0
000000404050  000a00000007 R_X86_64_JUMP_SLO 0000000000000000 fopen@GLIBC_2.2.5 + 0
000000404058  000b00000007 R_X86_64_JUMP_SLO 0000000000000000 __isoc99_scanf@GLIBC_2.7 + 0
000000404060  000c00000007 R_X86_64_JUMP_SLO 0000000000000000 exit@GLIBC_2.2.5 + 0
000000404068  000d00000007 R_X86_64_JUMP_SLO 0000000000000000 sleep@GLIBC_2.2.5 + 0
No processor specific unwind information to decode

Symbol table '.dynsym' contains 15 entries:
   Num:    Value          Size Type    Bind   Vis      Ndx Name
     0: 0000000000000000     0 NOTYPE  LOCAL  DEFAULT  UND 
     1: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND [...]@GLIBC_2.2.5 (2)
     2: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND puts@GLIBC_2.2.5 (2)
     3: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND [...]@GLIBC_2.2.5 (2)
     4: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND [...]@GLIBC_2.2.5 (2)
     5: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND fgetc@GLIBC_2.2.5 (2)
     6: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND [...]@GLIBC_2.2.5 (2)
     7: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND [...]@GLIBC_2.2.5 (2)
     8: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND __gmon_start__
     9: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND [...]@GLIBC_2.2.5 (2)
    10: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND fopen@GLIBC_2.2.5 (2)
    11: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND __[...]@GLIBC_2.7 (3)
    12: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND exit@GLIBC_2.2.5 (2)
    13: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND sleep@GLIBC_2.2.5 (2)
    14: 0000000000404080     8 OBJECT  GLOBAL DEFAULT   26 [...]@GLIBC_2.2.5 (2)

Symbol table '.symtab' contains 76 entries:
   Num:    Value          Size Type    Bind   Vis      Ndx Name
     0: 0000000000000000     0 NOTYPE  LOCAL  DEFAULT  UND 
     1: 0000000000400318     0 SECTION LOCAL  DEFAULT    1 .interp
     2: 0000000000400338     0 SECTION LOCAL  DEFAULT    2 .note.gnu.property
     3: 0000000000400358     0 SECTION LOCAL  DEFAULT    3 .note.gnu.build-id
     4: 000000000040037c     0 SECTION LOCAL  DEFAULT    4 .note.ABI-tag
     5: 00000000004003a0     0 SECTION LOCAL  DEFAULT    5 .gnu.hash
     6: 00000000004003c8     0 SECTION LOCAL  DEFAULT    6 .dynsym
     7: 0000000000400530     0 SECTION LOCAL  DEFAULT    7 .dynstr
     8: 00000000004005ca     0 SECTION LOCAL  DEFAULT    8 .gnu.version
     9: 00000000004005e8     0 SECTION LOCAL  DEFAULT    9 .gnu.version_r
    10: 0000000000400618     0 SECTION LOCAL  DEFAULT   10 .rela.dyn
    11: 0000000000400660     0 SECTION LOCAL  DEFAULT   11 .rela.plt
    12: 0000000000401000     0 SECTION LOCAL  DEFAULT   12 .init
    13: 0000000000401020     0 SECTION LOCAL  DEFAULT   13 .plt
    14: 00000000004010e0     0 SECTION LOCAL  DEFAULT   14 .plt.sec
    15: 0000000000401190     0 SECTION LOCAL  DEFAULT   15 .text
    16: 0000000000401448     0 SECTION LOCAL  DEFAULT   16 .fini
    17: 0000000000402000     0 SECTION LOCAL  DEFAULT   17 .rodata
    18: 000000000040209c     0 SECTION LOCAL  DEFAULT   18 .eh_frame_hdr
    19: 00000000004020f0     0 SECTION LOCAL  DEFAULT   19 .eh_frame
    20: 0000000000403e10     0 SECTION LOCAL  DEFAULT   20 .init_array
    21: 0000000000403e18     0 SECTION LOCAL  DEFAULT   21 .fini_array
    22: 0000000000403e20     0 SECTION LOCAL  DEFAULT   22 .dynamic
    23: 0000000000403ff0     0 SECTION LOCAL  DEFAULT   23 .got
    24: 0000000000404000     0 SECTION LOCAL  DEFAULT   24 .got.plt
    25: 0000000000404070     0 SECTION LOCAL  DEFAULT   25 .data
    26: 0000000000404080     0 SECTION LOCAL  DEFAULT   26 .bss
    27: 0000000000000000     0 SECTION LOCAL  DEFAULT   27 .comment
    28: 0000000000000000     0 FILE    LOCAL  DEFAULT  ABS crtstuff.c
    29: 00000000004011d0     0 FUNC    LOCAL  DEFAULT   15 deregister_tm_clones
    30: 0000000000401200     0 FUNC    LOCAL  DEFAULT   15 register_tm_clones
    31: 0000000000401240     0 FUNC    LOCAL  DEFAULT   15 __do_global_dtors_aux
    32: 0000000000404088     1 OBJECT  LOCAL  DEFAULT   26 completed.8061
    33: 0000000000403e18     0 OBJECT  LOCAL  DEFAULT   21 __do_global_dtor[...]
    34: 0000000000401270     0 FUNC    LOCAL  DEFAULT   15 frame_dummy
    35: 0000000000403e10     0 OBJECT  LOCAL  DEFAULT   20 __frame_dummy_in[...]
    36: 0000000000000000     0 FILE    LOCAL  DEFAULT  ABS picker-IV.c
    37: 0000000000000000     0 FILE    LOCAL  DEFAULT  ABS crtstuff.c
    38: 000000000040222c     0 OBJECT  LOCAL  DEFAULT   19 __FRAME_END__
    39: 0000000000000000     0 FILE    LOCAL  DEFAULT  ABS 
    40: 0000000000403e18     0 NOTYPE  LOCAL  DEFAULT   20 __init_array_end
    41: 0000000000403e20     0 OBJECT  LOCAL  DEFAULT   22 _DYNAMIC
    42: 0000000000403e10     0 NOTYPE  LOCAL  DEFAULT   20 __init_array_start
    43: 000000000040209c     0 NOTYPE  LOCAL  DEFAULT   18 __GNU_EH_FRAME_HDR
    44: 0000000000404000     0 OBJECT  LOCAL  DEFAULT   24 _GLOBAL_OFFSET_TABLE_
    45: 0000000000401440     5 FUNC    GLOBAL DEFAULT   15 __libc_csu_fini
    46: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND putchar@@GLIBC_2.2.5
    47: 0000000000404080     8 OBJECT  GLOBAL DEFAULT   26 stdout@@GLIBC_2.2.5
    48: 0000000000404070     0 NOTYPE  WEAK   DEFAULT   25 data_start
    49: 0000000000401276    40 FUNC    GLOBAL DEFAULT   15 print_segf_message
    50: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND puts@@GLIBC_2.2.5
    51: 0000000000404080     0 NOTYPE  GLOBAL DEFAULT   25 _edata
    52: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND fclose@@GLIBC_2.2.5
    53: 0000000000401448     0 FUNC    GLOBAL HIDDEN    16 _fini
    54: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND printf@@GLIBC_2.2.5
    55: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND fgetc@@GLIBC_2.2.5
    56: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND __libc_start_mai[...]
    57: 0000000000404070     0 NOTYPE  GLOBAL DEFAULT   25 __data_start
    58: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND signal@@GLIBC_2.2.5
    59: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND __gmon_start__
    60: 0000000000404078     0 OBJECT  GLOBAL HIDDEN    25 __dso_handle
    61: 0000000000402000     4 OBJECT  GLOBAL DEFAULT   17 _IO_stdin_used
    62: 00000000004013d0   101 FUNC    GLOBAL DEFAULT   15 __libc_csu_init
    63: 000000000040129e   150 FUNC    GLOBAL DEFAULT   15 win
    64: 0000000000404090     0 NOTYPE  GLOBAL DEFAULT   26 _end
    65: 00000000004011c0     5 FUNC    GLOBAL HIDDEN    15 _dl_relocate_sta[...]
    66: 0000000000401190    47 FUNC    GLOBAL DEFAULT   15 _start
    67: 0000000000404080     0 NOTYPE  GLOBAL DEFAULT   26 __bss_start
    68: 0000000000401334   144 FUNC    GLOBAL DEFAULT   15 main
    69: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND setvbuf@@GLIBC_2.2.5
    70: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND fopen@@GLIBC_2.2.5
    71: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND __isoc99_scanf@@[...]
    72: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND exit@@GLIBC_2.2.5
    73: 0000000000404080     0 OBJECT  GLOBAL HIDDEN    25 __TMC_END__
    74: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND sleep@@GLIBC_2.2.5
    75: 0000000000401000     0 FUNC    GLOBAL HIDDEN    12 _init

Histogram for `.gnu.hash' bucket list length (total of 2 buckets):
 Length  Number     % of total  Coverage
      0  1          ( 50.0%)
      1  1          ( 50.0%)    100.0%

Version symbols section '.gnu.version' contains 15 entries:
 Addr: 0x00000000004005ca  Offset: 0x000005ca  Link: 6 (.dynsym)
  000:   0 (*local*)       2 (GLIBC_2.2.5)   2 (GLIBC_2.2.5)   2 (GLIBC_2.2.5)
  004:   2 (GLIBC_2.2.5)   2 (GLIBC_2.2.5)   2 (GLIBC_2.2.5)   2 (GLIBC_2.2.5)
  008:   0 (*local*)       2 (GLIBC_2.2.5)   2 (GLIBC_2.2.5)   3 (GLIBC_2.7)  
  00c:   2 (GLIBC_2.2.5)   2 (GLIBC_2.2.5)   2 (GLIBC_2.2.5)

Version needs section '.gnu.version_r' contains 1 entry:
 Addr: 0x00000000004005e8  Offset: 0x000005e8  Link: 7 (.dynstr)
  000000: Version: 1  File: libc.so.6  Cnt: 2
  0x0010:   Name: GLIBC_2.7  Flags: none  Version: 3
  0x0020:   Name: GLIBC_2.2.5  Flags: none  Version: 2

Displaying notes found in: .note.gnu.property
  Owner                Data size        Description
  GNU                  0x00000010       NT_GNU_PROPERTY_TYPE_0
      Properties: x86 feature: IBT, SHSTK

Displaying notes found in: .note.gnu.build-id
  Owner                Data size        Description
  GNU                  0x00000014       NT_GNU_BUILD_ID (unique build ID bitstring)
    Build ID: 12b33c5ff389187551aae5774324da558cee006c

Displaying notes found in: .note.ABI-tag
  Owner                Data size        Description
  GNU                  0x00000010       NT_GNU_ABI_TAG (ABI version tag)
    OS: Linux, ABI: 3.2.0

┌──(kali㉿kali)-[~/picoCTF/reversing2]
└─$ readelf -a picker-IV | grep win
No processor specific unwind information to decode
    63: 000000000040129e   150 FUNC    GLOBAL DEFAULT   15 win


```

```bash
┌──(kali㉿kali)-[~/picoCTF/reversing2]
└─$ nc saturn.picoctf.net 60687
Enter the address in hex to jump to, excluding '0x': 40129e
You input 0x40129e
You won!
picoCTF{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_14bc5444}

```

## Forma 2
```bash
┌──(kali㉿kali)-[~/picoCTF/reversing2]
└─$ gdb picker-IV 
GNU gdb (Debian 15.1-1) 15.1
Copyright (C) 2024 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
--Type <RET> for more, q to quit, c to continue without paging--infofunctions:
Reading symbols from picker-IV...
(gdb) info functions
All defined functions:

Non-debugging symbols:
0x0000000000401000  _init
0x00000000004010e0  putchar@plt
0x00000000004010f0  puts@plt
0x0000000000401100  fclose@plt
0x0000000000401110  printf@plt
0x0000000000401120  fgetc@plt
0x0000000000401130  signal@plt
0x0000000000401140  setvbuf@plt
0x0000000000401150  fopen@plt
0x0000000000401160  __isoc99_scanf@plt
0x0000000000401170  exit@plt
0x0000000000401180  sleep@plt
--Type <RET> for more, q to quit, c to continue without paging--
0x0000000000401190  _start
0x00000000004011c0  _dl_relocate_static_pie
0x00000000004011d0  deregister_tm_clones
0x0000000000401200  register_tm_clones
0x0000000000401240  __do_global_dtors_aux
0x0000000000401270  frame_dummy
0x0000000000401276  print_segf_message
0x000000000040129e  win
0x0000000000401334  main
0x00000000004013d0  __libc_csu_init
0x0000000000401440  __libc_csu_fini
0x0000000000401448  _fini

```
Obtenemos la direccion de la funcion win
## Notas Adicionales

## Referencias
