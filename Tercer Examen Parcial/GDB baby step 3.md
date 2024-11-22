## Descripción 
```
Now for something a little different. `0x2262c96b` is loaded into memory in the `main` function. Examine byte-wise the memory that the constant is loaded in by using the GDB command `x/4xb addr`. The flag is the four bytes as they are stored in memory. If you find the bytes `0x11 0x22 0x33 0x44` in the memory location, your flag would be: `picoCTF{0x11223344}`.Debug [this](https://artifacts.picoctf.net/c/531/debugger0_c).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb3$ wget https://artifacts.picoctf.net/c/531/debugger0_c
--2024-11-21 13:57:21--  https://artifacts.picoctf.net/c/531/debugger0_c
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb3$ ls -la
total 24
drwxr-xr-x 2 porti_04 porti_04  4096 Nov 21 13:57 .
drwxr-xr-x 3 porti_04 porti_04  4096 Nov 21 13:57 ..
-rw-r--r-- 1 porti_04 porti_04 16304 Aug  4  2023 debugger0_c
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb3$ chmod +x debugger0_c
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb3$ gdb debugger0_c
GNU gdb (Ubuntu 12.1-0ubuntu1~22.04.2) 12.1
Copyright (C) 2022 Free Software Foundation, Inc.
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
Reading symbols from debugger0_c...
(No debugging symbols found in debugger0_c)
(gdb) break main
Breakpoint 1 at 0x40110e
(gdb) start
Temporary breakpoint 2 at 0x40110e
Starting program: /home/porti_04/pico_retos/tercer_parcial/gdb3/debugger0_c
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, 0x000000000040110e in main ()
(gdb) disas main
Dump of assembler code for function main:
   0x0000000000401106 <+0>:     endbr64
   0x000000000040110a <+4>:     push   %rbp
   0x000000000040110b <+5>:     mov    %rsp,%rbp
=> 0x000000000040110e <+8>:     mov    %edi,-0x14(%rbp)
   0x0000000000401111 <+11>:    mov    %rsi,-0x20(%rbp)
   0x0000000000401115 <+15>:    movl   $0x2262c96b,-0x4(%rbp)
   0x000000000040111c <+22>:    mov    -0x4(%rbp),%eax
   0x000000000040111f <+25>:    pop    %rbp
   0x0000000000401120 <+26>:    ret
End of assembler dump.
(gdb) brealk *0x000000000040111f
Undefined command: "brealk".  Try "help".
(gdb) break *0x000000000040111f
Breakpoint 3 at 0x40111f
(gdb) c
Continuing.

Breakpoint 3, 0x000000000040111f in main ()
(gdb) x/4xb $rbp-4
0x7fffffffda8c: 0x6b    0xc9    0x62    0x22

flag: **picoCTF{0x6bc96222}**
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias