## Descripción 
```
I wonder what this really is... [enc](https://mercury.picoctf.net/static/2b4cea9b07db22bf4f933fddd1b8caa9/enc) `''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])`
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/t$ wget https://mercury.picoctf.net/static/2b4cea9b07db22bf4f933fddd1b8caa9/enc
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/t$ cat enc
灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸弰㑣〷㘰摽porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/t$ nano
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/t$ python3 solve.py enc
Flag: picoCTF{16_bits_inst34d_of_8_04c0760d}
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/t$ cat solve.py
encoded_flag = open("enc").read()
flag = ""
for i in range(0, len(encoded_flag)):
    character1 = chr((ord(encoded_flag[i]) >> 8))
    character2 = chr(encoded_flag[i].encode('utf-16be')[-1])
    flag += character1
    flag += character2

print("Flag: " + flag)
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/t$

flag: picoCTF{16_bits_inst34d_of_8_04c0760d}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias