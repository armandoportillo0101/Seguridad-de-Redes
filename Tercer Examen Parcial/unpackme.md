## Descripción 
```
Can you get the flag?Reverse engineer this [binary](https://artifacts.picoctf.net/c/204/unpackme-upx).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial$ cd unpackme
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/unpackme$ ls -la
total 380
drwxr-xr-x 2 porti_04 porti_04   4096 Nov 21 14:55 .
drwxr-xr-x 3 porti_04 porti_04   4096 Nov 21 14:55 ..
-rw-r--r-- 1 porti_04 porti_04 379188 Aug  4  2023 unpackme-upx
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/unpackme$ ./upx-4.0.2-amd64_linux/upx -d unpackme-upx
                       Ultimate Packer for eXecutables
                          Copyright (C) 1996 - 2023
UPX 4.0.2       Markus Oberhumer, Laszlo Molnar & John Reiser   Jan 30th 2023

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
   1006445 <-    379188   37.68%   linux/amd64   unpackme-upx

Unpacked 1 file.
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/unpackme$ gdb ./unpackme-upx
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
Reading symbols from ./unpackme-upx...
(No debugging symbols found in ./unpackme-upx)
(gdb) layout asm
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/unpackme$ ./unpackme-upx
What's my favorite number? 754635
picoCTF{up><_m3_f7w_e510a27f}

flag: picoCTF{up><_m3_f7w_e510a27f}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Sabemos que el programa pide un número y luego probablemente imprimirá la bandera si se le da el número correcto. Por lo tanto, estamos buscando una `cmp`instrucción. Vemos `<+133>: cmp $0xb83cb,%eax`. La conversión `b83cb`de hexadecimal a decimal da como resultado `754635`.

Al ejecutar el programa e ingresarlo `754635`se imprime la bandera.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias