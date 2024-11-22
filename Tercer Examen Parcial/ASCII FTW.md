## Descripción 
```
This program has constructed the flag using hex ascii values. Identify the flag text by disassembling the program.You can download the file from [here](https://artifacts.picoctf.net/c/508/asciiftw).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial$ cd ascii
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ascii$ wget https://artifacts.picoctf.net/c/508/asciiftw
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ascii$ file asciiftw
asciiftw: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=e1c32dace8ac1516160b771e493f5ebffcac9855, for GNU/Linux 3.2.0, not stripped
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ascii$ ./asciiftw
-bash: ./asciiftw: Permission denied
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ascii$ chmod +x asciiftw
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ascii$ ./asciiftw
The flag starts with 70
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ascii$ gdb ./asciiftw
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
Reading symbols from ./asciiftw...
(No debugging symbols found in ./asciiftw)
(gdb) layout next

flag: picoCTF{ASCII_IS_EASY_8960F0AF}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Al abrir gdb  y ejecutar "layout next" en la funcion main se declaran 31 variables en la pila: 
0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x41 0x53 0x43 0x49 0x49 0x5f 0x49 0x53 0x5f 0x45 0x41 0x53 0x59 0x5f 0x38 0x39 0x36 0x30 0x46 0x30 0x41 0x46 0x7d
ya solo los converti en cyber chef de hexadecimal a texto
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias