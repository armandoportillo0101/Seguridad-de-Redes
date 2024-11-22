## Descripción 
```
`main` calls a function that multiplies `eax` by a constant. The flag for this challenge is that constant in decimal base. If the constant you find is 0x1000, the flag will be `picoCTF{4096}`.Debug [this](https://artifacts.picoctf.net/c/532/debugger0_d).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb4$ wget https://artifacts.picoctf.net/c/532/debugger0_d
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb4$ ls -la
total 24
drwxr-xr-x 2 porti_04 porti_04  4096 Nov 21 14:13 .
drwxr-xr-x 3 porti_04 porti_04  4096 Nov 21 14:12 ..
-rw-r--r-- 1 porti_04 porti_04 16328 Aug  4  2023 debugger0_d
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb4$ chmod +x debugger0_d
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb4$ gdb --args ./debugger0_d
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
Reading symbols from ./debugger0_d...
(No debugging symbols found in ./debugger0_d)
(gdb) layout asm
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb4$ printf "picoCTF{%d}\n" 0x3269 | tee flag.txt
picoCTF{12905}

flag: picoCTF{12905}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
En main+38 va a func1 y en func1+14 tiene una accion imul que significa multiplicacion y se hace en eax. El numero es 0x3269 y al salir de gdb con 'q' puedes poner el siguiente comando para obtener la bandera:

`printf "picoCTF{%d}\n" 0x3269 | tee flag.txt`
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias