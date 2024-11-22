## Descripción 
```
You will find the flag after decrypting this fileDownload the encrypted flag [here](https://artifacts.picoctf.net/c/385/encrypted.txt).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/rotation$ wget https://artifacts.picoctf.net/c/385/encrypted.txt
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/rotation$ cat encrypted.txt
xqkwKBN{z0bib1wv_l3kzgxb3l_555957n3}

flag: picoCTF{r0tat1on_d3crypt3d_555957f3}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
El nombre del desafío indica que tiene algo que ver con algún tipo de rotación. Con el uso de Google descubrimos que tiene algo que ver con el código ROT. Para descifrar estos caracteres aleatorios, usamos Cyberchef.

En primer lugar, usamos la fuerza bruta ROT13, porque es el cifrado ROT más común que se usa en un CTF. Al observar el resultado, podemos ver la bandera dentro.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias