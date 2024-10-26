## Descripción 
```
Download this image file and find the flag.

- [Download image file](https://artifacts.picoctf.net/c/101/drawing.flag.svg)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/enhance$ wget https://artifacts.picoctf.net/c/101/drawing.flag.svg
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/enhance$ #!/usr/bin/bash
strings drawing.flag.svg | grep "</tspan" | cut -d '>' -f2 | cut -d '<' -f1 | tr -d '\n' | tr -d ' '
picoCTF{3nh4nc3d_24374675}

flag: picoCTF{3nh4nc3d_24374675}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias