## Objetivo
```
What does this `bDNhcm5fdGgzX3IwcDM1` mean? I think it has something to do with bases.
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
El título y el enunciado del problema nos indican que se trata de otro problema de conversión de base. Una mezcla de caracteres y números indica que se trata de un valor con una base muy alta. Podemos intentar decodificarlo con una base grande común, como base64, que nos dará nuestra bandera. La forma más fácil de solucionarlo es simplemente pasarlo por un sitio en línea de conversión de base como CyberChef
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias
https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)To_Hex('Space',0/breakpoint)&input=YkROaGNtNWZkR2d6WDNJd2NETTE