## Descripción 
```
Not all ancient ciphers were so bad... The flag is not in standard format. `nc mercury.picoctf.net 19860` [playfair.py](https://mercury.picoctf.net/static/3f082e143dd5b4ffe1a0aaaf317872b8/playfair.py)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/playnice$ wget https://mercury.picoctf.net/static/3f082e143dd5b4ffe1a0aaaf317872b8/playfair.py
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/playnice$ cat playfair.py
#!/usr/bin/python3 -u
import signal

SQUARE_SIZE = 6


def generate_square(alphabet):
        assert len(alphabet) == pow(SQUARE_SIZE, 2)
        matrix = []
        for i, letter in enumerate(alphabet):
                if i % SQUARE_SIZE == 0:
                        row = []
                row.append(letter)
                if i % SQUARE_SIZE == (SQUARE_SIZE - 1):
                        matrix.append(row)
        return matrix

def get_index(letter, matrix):
        for row in range(SQUARE_SIZE):
                for col in range(SQUARE_SIZE):
                        if matrix[row][col] == letter:
                                return (row, col)
        print("letter not found in matrix.")
        exit()

def encrypt_pair(pair, matrix):
        p1 = get_index(pair[0], matrix)
        p2 = get_index(pair[1], matrix)

        if p1[0] == p2[0]:
                return matrix[p1[0]][(p1[1] + 1)  % SQUARE_SIZE] + matrix[p2[0]][(p2[1] + 1)  % SQUARE_SIZE]
        elif p1[1] == p2[1]:
                return matrix[(p1[0] + 1)  % SQUARE_SIZE][p1[1]] + matrix[(p2[0] + 1)  % SQUARE_SIZE][p2[1]]
        else:
                return matrix[p1[0]][p2[1]] + matrix[p2[0]][p1[1]]

def encrypt_string(s, matrix):
        result = ""
        if len(s) % 2 == 0:
                plain = s
        else:
                plain = s + "lsi28c14ot0vbf7nagh3mpjuxy5kwz6edqr9"[0]
        for i in range(0, len(plain), 2):
                result += encrypt_pair(plain[i:i + 2], matrix)
        return result

alphabet = open("key").read().rstrip()
m = generate_square(alphabet)
msg = open("msg").read().rstrip()
enc_msg = encrypt_string(msg, m)
print("Here is the alphabet: {}\nHere is the encrypted message: {}".format(alphabet, enc_msg))
signal.alarm(18)
resp = input("What is the plaintext message? ").rstrip()
if resp and resp == msg:
        print("Congratulations! Here's the flag: {}".format(open("flag").read()))

# https://en.wikipedia.org/wiki/Playfair_cipher
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/playnice$ nc mercury.picoctf.net 19860
Here is the alphabet: lsi28c14ot0vbf7nagh3mpjuxy5kwz6edqr9
Here is the encrypted message: 1x5hqlod8x7oa88h0de1b5r6xja5sd

porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/playnice$ nano
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/playnice$ python3 solve.py
now i= 0
now i= 2
now i= 4
now i= 6
now i= 8
now i= 10
now i= 12
now i= 14
now i= 16
now i= 18
now i= 20
now i= 22
now i= 24
now i= 26
now i= 28
lhxm62i5lwoi0rljor647xq9wh7wie
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/playnice$ nc mercury.picoctf.net 19860
Here is the alphabet: lsi28c14ot0vbf7nagh3mpjuxy5kwz6edqr9
Here is the encrypted message: 1x5hqlod8x7oa88h0de1b5r6xja5sd
What is the plaintext message? lhxm62i5lwoi0rljor647xq9wh7wie
Congratulations! Here's the flag: f391b621282ef5063ab2de93ab9e4bff
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/playnice$ cat solve.py
SQUARE_SIZE = 6
def generate_square(alphabet):
        assert len(alphabet) == pow(SQUARE_SIZE, 2) #can be ignored here
        matrix = []
        for i, letter in enumerate(alphabet):
                if i % SQUARE_SIZE == 0: #i%6==0
                        row = []
                row.append(letter)
                if i % SQUARE_SIZE == (SQUARE_SIZE - 1):
                        matrix.append(row)
        return matrix

def get_index(letter, matrix):
        for row in range(SQUARE_SIZE):
                for col in range(SQUARE_SIZE):
                        if matrix[row][col] == letter:
                                return (row, col)
        print("letter not found in matrix.")
        exit()

def decrypt_pair(pair, matrix):
        #print("pair=",pair)
        p1 = get_index(pair[0], matrix) #(row,col)
        p2 = get_index(pair[1], matrix) #(row,col)

        if p1[0] == p2[0]: #same row
                return matrix[p1[0]][(p1[1] - 1)  % SQUARE_SIZE] + matrix[p2[0]][(p2[1] - 1)  % SQUARE_SIZE]
        elif p1[1] == p2[1]: #same col
                return matrix[(p1[0] - 1)  % SQUARE_SIZE][p1[1]] + matrix[(p2[0] - 1)  % SQUARE_SIZE][p2[1]]
        else: #neither
                return matrix[p1[0]][p2[1]] + matrix[p2[0]][p1[1]]

def decrypt_string(s, matrix):
        result = ""
        for i in range(0, len(s), 2):
                print("now i=",i)
                result += decrypt_pair(s[i:i + 2], matrix)
        return result

alphabet = "lsi28c14ot0vbf7nagh3mpjuxy5kwz6edqr9"
m = generate_square(alphabet) #key table
enc_msg="1x5hqlod8x7oa88h0de1b5r6xja5sd"
msg=decrypt_string(enc_msg,m)
print(msg)

flag:  f391b621282ef5063ab2de93ab9e4bff

```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias