## Descripción 
```
We found a brand new type of encryption, can you break the secret code? (Wrap with picoCTF{}) `mlnklfnknljflfjljnjijjmmjkmljnjhmhjgjnjjjmmkjjmijhmkjhjpmkmkmljkjijnjpmhmjjgjj` [new_caesar.py](https://mercury.picoctf.net/static/43182e6d4527ef0916b2ce43883227b7/new_caesar.py)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ncaesar$ wget https://mercury.picoctf.net/static/43182e6d4527ef0916b2ce43883227b7/new_caesar.py
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ncaesar$ nano new_caesar.py
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ncaesar$ nano new_caesar.py
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ncaesar$ cat new_caesar.py
import string

LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

def b16_encode(plain):
        enc = ""
        for c in plain:
                binary = "{0:08b}".format(ord(c))
                enc += ALPHABET[int(binary[:4], 2)]
                enc += ALPHABET[int(binary[4:], 2)]
        return enc

def shift(c, k):
        t1 = ord(c) - LOWERCASE_OFFSET
        t2 = ord(k) - LOWERCASE_OFFSET
        return ALPHABET[(t1 + t2) % len(ALPHABET)]

flag = "redacted"
key = "redacted"
assert all([k in ALPHABET for k in key])
assert len(key) == 1

b16 = b16_encode(flag)
enc = ""
for i, c in enumerate(b16):
        enc += shift(c, key[i % len(key)])
print(enc)
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ncaesar$ python3 new_caesar.py
78
Traceback (most recent call last):
  File "/home/porti_04/pico_retos/tercer_parcial/ncaesar/new_caesar.py", line 28, in <module>
    b16 = b16_decode(dec)
NameError: name 'b16_decode' is not defined. Did you mean: 'b16_encode'?
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ncaesar$ cat new_caesar.py
import string

LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

def b16_encode(plain):
        enc = ""
        for c in plain:
                binary = "{0:08b}".format(ord(c))
                enc += ALPHABET[int(binary[:4], 2)]
                enc += ALPHABET[int(binary[4:], 2)]
        return enc

def shift(c, k):
        t1 = ord(c) - LOWERCASE_OFFSET
        t2 = ord(k) - LOWERCASE_OFFSET
        return ALPHABET[(t1 + t2) % len(ALPHABET)]

encflag =  "mlnklfnknljflfjljnjijjmmjkmljnjhmhjgjnjjjmmkjjmijhmkjhjpmkmkmljkjijnjpmhmjjgjj"
#assert all([k in ALPHABET for k in key])
#assert len(key) == 1

print(len(encflag))
for key in ALPHABET:
        dec  = ""
        for c in encflag:
                dec += shift(c, key)
        b16 = b16_decode(dec)
        print(key, b16)
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ncaesar$ nano
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/ncaesar$ python3 solve.py
78
Key: a, Decoded: ËÚµÚÛµÌËÇÊÈÊÊÊËÇÉ
Key: b, Decoded: ºÉ¤ÉÊ¤»º¶¹·¹¹¹º¶¸
Key: c, Decoded: ©¸¸¹sy{vwªx©{u¥t{wz¨w¦u¨u}¨¨©xv{}¥§tw
Key: d, Decoded: §§¨bhjefgjdcjfifddlgejlcf
Key: e, Decoded: qQqWYTUVYSRYUXUSS[VTY[RU
Key: f, Decoded: v`@`FHCDwEvHBrAHDGuDsBuBJuuvECHJrtAD
Key: g, Decoded: et_tu?_5723f4e71a0736d3b1d19dde4279ac03
Key: h, Decoded: TcNcd.N$&!"U#T& P/&"%S"Q S (SST#!&(PR/"
Key: i, Decoded: CR=RS=DCOB@BBBCOA
Key: j, Decoded: 2A,AB
1?1112>0              ,32>
Key: k, Decoded: !01ûóþÿ"ð!óý-üóÿò ÿ.ý ýõ  !ðþóõ-/üÿ
Key: l, Decoded: /
/ ê
àâíîïâìëâîáîììäïíâäëî
Key: m, Decoded: ùÙùßÑÜÝÞÑÛ
                           ÚÑÝÐÝ
                                ÛÛÓÞÜÑÓ
ÚÝ
ÈèÎÀËÌÿÍþÀÊúÉÀÌÏýÌûÊýÊÂýýþÍËÀÂúüÉÌ
Key: o, Decoded: íü×üý·×½¿º»î¼í¿¹é¸¿»¾ì»ê¹ì¹±ììí¼º¿±éë¸»
Key: p, Decoded: ÜëÆëì¦Æ¬®©ªÝ«Ü®¨Ø§®ª­ÛªÙ¨Û¨ ÛÛÜ«©® ØÚ§ª

flag: picoCTF{et_tu?_5723f4e71a0736d3b1d19dde4279ac03}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Esto es lo que contiene el archivo de solve.py: 
import string

LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

def b16_encode(plain):
    enc = ""
    for c in plain:
        binary = "{0:08b}".format(ord(c))
        enc += ALPHABET[int(binary[:4], 2)]
        enc += ALPHABET[int(binary[4:], 2)]
    return enc

def b16_decode(encoded):
    plain = ""
    for i in range(0, len(encoded), 2):
        high = ALPHABET.index(encoded[i])  # Primer carácter (4 bits altos)
        low = ALPHABET.index(encoded[i + 1])  # Segundo carácter (4 bits bajos)
        binary = (high << 4) | low  # Reconstruir los 8 bits del carácter
        plain += chr(binary)
    return plain

def shift_back(c, k):
    t1 = ord(c) - LOWERCASE_OFFSET
    t2 = ord(k) - LOWERCASE_OFFSET
    return ALPHABET[(t1 - t2) % len(ALPHABET)]  # Operación inversa de `shift`

encflag = "mlnklfnknljflfjljnjijjmmjkmljnjhmhjgjnjjjmmkjjmijhmkjhjpmkmkmljkjijnjpmhmjjgjj"
print(len(encflag))

for key in ALPHABET:
    dec = ""
    for c in encflag:
        dec += shift_back(c, key)  # Usar la operación inversa de `shift`
    try:
        b16 = b16_decode(dec)  # Decodificar el texto base16
        print(f"Key: {key}, Decoded: {b16}")
    except Exception as e:
        print(f"Key: {key}, Error: {e}")
    
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)
Como se nos dan varias posibles banderas, hay que escoger la bandera que parezca mas coherente.
### Referencias