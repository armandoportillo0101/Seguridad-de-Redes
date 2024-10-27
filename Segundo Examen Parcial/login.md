## Descripción 
```
My dog-sitter's brother made this website but I can't get in; can you help?[login.mars.picoctf.net](https://login.mars.picoctf.net/)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
Fui al código fuente, incluido el JavaScript detrás del formulario. Encontré index.js.
El método for y la línea de retorno son lo que me parece interesante. Primero descubro lo que hace btoa, supongo que se trata de alguna codificación. Parece que esta función codifica una cadena en base 64, como leí [aquí](https://developer.mozilla.org/en-US/docs/Web/API/btoa) . También veo que hay una función atob que decodifica la base 64 a ASCII. Intento decodificar algunas de las cadenas de caracteres ilusorias en el código fuente para ver si puedo encontrar un nombre de usuario o una contraseña.

Cuando decodifiqué la cadena “cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ”, encontré la bandera. Puedes decodificarla a través de un sitio web, el cual puse en la referencias

flag: picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias
https://www.base64decode.org/](https://www.base64decode.org/