## Descripción 
```
I just recently learnt about the SRA public key cryptosystem... or wait, was it supposed to be RSA? Hmmm, I should probably check...Connect to the program on our server: `nc saturn.picoctf.net 50869`Download the program: [chal.py](https://artifacts.picoctf.net/c/295/chal.py)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~$ cd pico_retos
porti_04@DESKTOP-8HT902T:~/pico_retos$ cd tercer_parcial
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial$ cd SRA
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/SRA$ ls -la
total 16
drwxr-xr-x 2 porti_04 porti_04 4096 Nov 21 23:22 .
drwxr-xr-x 3 porti_04 porti_04 4096 Nov 21 22:56 ..
-rw-r--r-- 1 porti_04 porti_04  630 Aug  4  2023 chal.py
-rw-r--r-- 1 porti_04 porti_04 2048 Nov 21 23:22 solve.py
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/SRA$ nc saturn.picoctf.net 60114
anger = 70249053533380461456279408551338695455573508828740250823796159249793848746766
envy = 42130202602804328223330138233527296794844628606757891214506381783316142656353
vainglory?
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/SRA$ nano
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/SRA$ pip install pycryptodome
Defaulting to user installation because normal site-packages is not writeable
Requirement already satisfied: pycryptodome in /home/porti_04/.local/lib/python3.10/site-packages (3.21.0)
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/SRA$ python3 solucion.py
[+] Opening connection to saturn.picoctf.net on port 60114: Done
Factoring...
[*] Switching to interactive mode
NYimht7AaJNVgfUj
Conquered!
picoCTF{7h053_51n5_4r3_n0_m0r3_2b7ad1ae}
[*] Got EOF while reading in interactive

flag: picoCTF{7h053_51n5_4r3_n0_m0r3_2b7ad1ae}

```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Este el script que hice para sacar la bandera del reto: 
```
from sympy import factorint  # Importar factorint de sympy
from Crypto.Util.number import getPrime, inverse, bytes_to_long, isPrime, long_to_bytes  # Importar long_to_bytes
from string import ascii_letters, digits
from random import choice
from pwn import remote
from itertools import combinations
from functools import reduce

# Función para obtener el producto de una lista de números
def product(iterable):
    return reduce(lambda x, y: x * y, iterable, 1)

# Conectar al servidor
con = remote("saturn.picoctf.net", 60114)
e = 65537

# Obtener el ciphertext
con.recvuntil(b'anger = ')
c = int(con.readline().decode())

# Obtener d
con.recvuntil(b'envy = ')
d = int(con.readline().decode())

print('Factoring...')

# Intentar factorizar d*e - 1
fac = [a for a, b in list(factorint(d * e - 1).items()) for _ in range(b)]

# Intentar todas las combinaciones de factores
for r in range(2, len(fac)):
    for i in combinations(fac, r):
        p = product(i) + 1  # Producto de los factores más 1
        if p.bit_length() != 128 or not isPrime(p):
            continue
        m = long_to_bytes(pow(c, d, p))  # Decodificar el mensaje
        if len(m) != 16:
            continue
        con.recvuntil(b'> ')
        con.sendline(m)  # Enviar el mensaje decodificado
        con.interactive()  # Interactuar con el servidor
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias