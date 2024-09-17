## Objetivo
```
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/94d00153b0057d37da225ee79a846c62/strings) without running it?
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~$https://jupiter.challenges.picoctf.org/static/94d00153b0057d37da225ee79a846c62/strings
porti_04@DESKTOP-8HT902T:~$ ls
strings
porti_04@DESKTOP-8HT902T:~$ strings strings | grep picoCTF
picoCTF{5tRIng5_1T_d66c7bb7}
porti_04@DESKTOP-8HT902T:~$

```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
El comando `strings strings | grep picoCTF` busca el texto "picoCTF" dentro del contenido legible de un archivo llamado `strings`.

- **`strings strings`**: Extrae todas las secuencias de texto legible del archivo llamado `strings`. Esto es útil cuando el archivo `strings` es binario o no es directamente legible.
- **`| grep picoCTF`**: Filtra el resultado para mostrar solo las líneas que contienen la palabra "picoCTF", que a menudo está relacionada con retos de captura de la bandera (CTF) en competencias de seguridad informática.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias