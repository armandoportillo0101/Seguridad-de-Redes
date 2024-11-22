## Descripción 
```
[crackme.py](https://mercury.picoctf.net/static/b7cabaae6561256c50728d3515db3058/crackme.py)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/creakme$ wget https://mercury.picoctf.net/static/b7cabaae6561256c50728d3515db3058/crackme.py
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/creakme$ nano crackme.py
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/creakme$ cat crackme.py
# Hiding this really important number in an obscure piece of code is brilliant!
# AND it's encrypted!
# We want our biggest client to know his information is safe with us.
bezos_cc_secret = "A:4@r%uL`M-^M0c0AbcM-MFE07b34c`_6N"

# Reference alphabet
alphabet = "!\"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ"+ \
            "[\\]^_`abcdefghijklmnopqrstuvwxyz{|}~"



def decode_secret(secret):
    """ROT47 decode

    NOTE: encode and decode are the same operation in the ROT cipher family.
    """

    # Encryption key
    rotate_const = 47

    # Storage for decoded secret
    decoded = ""

    # decode loop
    for c in secret:
        index = alphabet.find(c)
        original_index = (index + rotate_const) % len(alphabet)
        decoded = decoded + alphabet[original_index]

    print(decoded)



def choose_greatest():
    """Echo the largest of the two numbers given by the user to the program

    Warning: this function was written quickly and needs proper error handling
    """

    user_value_1 = input("What's your first number? ")
    user_value_2 = input("What's your second number? ")
    greatest_value = user_value_1 # need a value to return if 1 & 2 are equal

    if user_value_1 > user_value_2:
        greatest_value = user_value_1
    elif user_value_1 < user_value_2:
        greatest_value = user_value_2

    print( "The number with largest positive magnitude is "
        + str(greatest_value) )



choose_greatest()

flag: picoCTF{1|\/|_4_p34|\|ut_f3bc410e}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
En el script, busque la variablebezos_cc_secret = "A:4@r%uL`M-^M0c0AbcM-MFE07b34c`_6N . Esta contiene el mensaje secreto codificado que necesitamos decodificar.

- Notarás una función llamada `decode_secret`que menciona la " decodificación **ROT47** ". El cifrado ROT47 es un cifrado simple de sustitución de letras, donde cada carácter se desplaza 47 posiciones en la tabla ASCII.
- Visita el decodificador ROT47 en [**https://www.dcode.fr/rot-47-cipher**](https://www.dcode.fr/rot-47-cipher) **.**[](https://www.dcode.fr/rot-47-cipher)
- Copie el mensaje codificado bezos_cc_secret = "A:4@r%uL`M-^M0c0AbcM-MFE07b34c`_6N" del script y péguelo en el decodificador en línea.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias