## Descripción 
```
Can you decrypt this message?Decrypt this [message](https://artifacts.picoctf.net/c/160/cipher.txt) using this key "CYLAB".
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/vigenere$ wget https://artifacts.picoctf.net/c/160/cipher.txt
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/vigenere$ cat cipher.txt
rgnoDVD{O0NU_WQ3_G1G3O3T3_A1AH3S_2951c89f}
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/vigenere$ nano
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/vigenere$ nano solve.py
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/vigenere$ python3 solve.py
picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_2951a89h}

flag: picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_2951a89h}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Este es el contenido de solve.py, el archivo .py que saca la bandera: 
import string
instr="rgnoDVD{O0NU_WQ3_G1G3O3T3_A1AH3S_2951c89f}"
key="CYLAB"
outstr=""
offset_lower=ord('a')
offset_upper=ord('A')
lower=string.ascii_lowercase
upper=string.ascii_uppercase


dicts_l={}
for k in key:
    key_loc=ord(k)-offset_upper
    dicts_l[k]={}
    for l in lower:
        cipher=chr((ord(l)-offset_lower+key_loc)%26+offset_lower)
        dicts_l[k][cipher]=l #dicts_l[key][cipher]=[plain]


dicts_u = {}
for k in key:
    key_loc = ord(k) - offset_upper
    dicts_u[k] = {}
    for u in upper:
        dicts_u[k][chr((ord(u) - offset_upper + key_loc) % 26 + offset_upper)] = u  # dicts_u[key][cipher]=[p>

count=0
for c in instr:
    if c.isalpha():
        if c.islower():
            outstr+=dicts_l[key[count%len(key)]][c]
        elif c.isupper():
            outstr+=dicts_u[key[count%len(key)]][c]
        count+=1
    else:
        outstr+=c
print(outstr)

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias