## Objetivo
```
Can you find the flag in [file](strings files.zip | grep pico)? This would be really tedious to look through manually, something tells me there is a better way.
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~$ wget https://jupiter.challenges.picoctf.org/static/315d3325dc668ab7f1af9194f2de7e7a/file
porti_04@DESKTOP-8HT902T:~$ strings files | grep pico
strings: 'files': No such file
porti_04@DESKTOP-8HT902T:~$ strings file | grep pico
picoCTF{grep_is_good_to_find_things_f77e0797}
porti_04@DESKTOP-8HT902T:~$
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
El comando `strings file | grep pico` se usa para buscar texto legible dentro de un archivo binario o cualquier archivo que no sea directamente legible.

- **`strings file`**: Este comando extrae todas las secuencias de caracteres imprimibles (texto legible) del archivo especificado.
- **`| grep pico`**: Luego, pasa el resultado al comando `grep`, que busca la palabra o patrón `pico` dentro de esas secuencias de texto extraídas.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias