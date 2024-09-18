## Objetivo
```
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 14291`.
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
Después de conectarnos a este puerto, nos encontramos con muchas líneas de mensajes de relleno. Hee, podemos usar una tubería `|`. Lo que hace una tubería en el shell es permitirnos combinar dos comandos en uno. ENTONCES, si quisiéramos buscar el valor de retorno de la conexión del host netcat para un indicador, podemos ejecutar nc jupiter.challenges.picoctf.org 14291 | grep picoCTF
porti_04@DESKTOP-8HT902T:~$ nc jupiter.challenges.picoctf.org 14291 | grep picoCTF
picoCTF{digital_plumb3r_ea8bfec7}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
El comando **`nc jupiter.challenges.picoctf.org 14291 | grep picoCTF`** se utiliza para conectarse a un servidor remoto a través de la herramienta `nc` (netcat) y buscar la palabra **`picoCTF`** en la respuesta del servidor.

### Desglose:

- **`nc jupiter.challenges.picoctf.org 14291`**:
    
    - `nc` es el comando para usar netcat, que permite crear conexiones de red, tanto para enviar como recibir datos.
    - `jupiter.challenges.picoctf.org` es el nombre del servidor al que te conectas.
    - `14291` es el puerto en el servidor donde te conectas.
- **`| grep picoCTF`**:
    
    - Toma la salida de `nc` (lo que responde el servidor) y la filtra para buscar cualquier línea que contenga la palabra "picoCTF", que normalmente es parte de la bandera en retos de CTF.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias