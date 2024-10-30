## Descripción 
```
Can you figure out how this program works to get the flag?Connect to the program with netcat:`$ nc saturn.picoctf.net 62617`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/524/picker-III.py).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/reversing$ wget https://artifacts.picoctf.net/c/524/picker-III.py
porti_04@DESKTOP-8HT902T:~/pico_retos/reversing$ nano picker-III.py
porti_04@DESKTOP-8HT902T:~/pico_retos/reversing$ nc saturn.picoctf.net 62617
==> help

This program fixes vulnerabilities in its predecessor by limiting what
functions can be called to a table of predefined functions. This still puts
the user in charge, but prevents them from calling undesirable subroutines.

* Enter 'quit' to quit the program.
* Enter 'help' for this text.
* Enter 'reset' to reset the table.
* Enter '1' to execute the first function in the table.
* Enter '2' to execute the second function in the table.
* Enter '3' to execute the third function in the table.
* Enter '4' to execute the fourth function in the table.

Here's the current table:

1: print_table
2: read_variable
3: write_variable
4: getRandomNumber
==> 3
Please enter variable name to write: getRandomNumber
Please enter new value of variable: win
==> 4
0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x37 0x68 0x31 0x35 0x5f 0x31 0x35 0x5f 0x77 0x68 0x34 0x37 0x5f 0x77 0x33 0x5f 0x67 0x33 0x37 0x5f 0x77 0x31 0x37 0x68 0x5f 0x75 0x35 0x33 0x72 0x35 0x5f 0x31 0x6e 0x5f 0x63 0x68 0x34 0x72 0x67 0x33 0x5f 0x63 0x32 0x30 0x66 0x35 0x32 0x32 0x32 0x7d
==>


flag: picoCTF{7h15_15_wh47_w3_g37_w17h_u53r5_1n_ch4rg3_c20f5222}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Cuando se nos dió:
0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x37 0x68 0x31 0x35 0x5f 0x31 0x35 0x5f 0x77 0x68 0x34 0x37 0x5f 0x77 0x33 0x5f 0x67 0x33 0x37 0x5f 0x77 0x31 0x37 0x68 0x5f 0x75 0x35 0x33 0x72 0x35 0x5f 0x31 0x6e 0x5f 0x63 0x68 0x34 0x72 0x67 0x33 0x5f 0x63 0x32 0x30 0x66 0x35 0x32 0x32 0x32 0x7d

Está en hexadecimal, lo decodificamos en cyberchef
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias
https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')&input=MHg3MCAweDY5IDB4NjMgMHg2ZiAweDQzIDB4NTQgMHg0NiAweDdiIDB4MzcgMHg2OCAweDMxIDB4MzUgMHg1ZiAweDMxIDB4MzUgMHg1ZiAweDc3IDB4NjggMHgzNCAweDM3IDB4NWYgMHg3NyAweDMzIDB4NWYgMHg2NyAweDMzIDB4MzcgMHg1ZiAweDc3IDB4MzEgMHgzNyAweDY4IDB4NWYgMHg3NSAweDM1IDB4MzMgMHg3MiAweDM1IDB4NWYgMHgzMSAweDZlIDB4NWYgMHg2MyAweDY4IDB4MzQgMHg3MiAweDY3IDB4MzMgMHg1ZiAweDYzIDB4MzIgMHgzMCAweDY2IDB4MzUgMHgzMiAweDMyIDB4MzIgMHg3ZA