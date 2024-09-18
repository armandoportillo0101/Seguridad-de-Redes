## Objetivo
```
If I told you a word started with 0x70 in hexadecimal, what would it start with in ASCII?
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
**Método: Python**
Este método es ideal cuando ya estás trabajando en Python o estás en un entorno CLI. Python tiene una forma sencilla de convertir hexadecimal a ASCII, pero ten en cuenta que Python2 y Python3 tienen métodos diferentes.
porti_04@DESKTOP-8HT902T:~$ python3 -c "print(chr(0x70))"
p
bandera: picoCTF{p}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
El comando `python3 -c "print(chr(0x70))"` convierte el valor hexadecimal `0x70` al carácter ASCII correspondiente:

- **`chr(0x70)`**: Convierte el número hexadecimal `0x70` (equivalente a 112 en decimal) en el carácter ASCII, que es la letra **`p`**.
- **`print()`**: Imprime el resultado, que en este caso será la letra `p`.

En resumen, este comando imprime el carácter ASCII correspondiente al valor hexadecimal `0x70`, que es **`p`**.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias