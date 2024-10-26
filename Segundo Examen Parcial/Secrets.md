## Descripción 
```
We have several pages hidden. Can you find the one with the flag?The website is running [here](http://saturn.picoctf.net:53838/).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
Accedemos a la herramienta “Inspeccionar” haciendo clic derecho. Si vamos a las fuentes, podemos ver los archivos que se encuentran dentro del directorio assets. Observamos que el directorio assets se encuentra dentro de un directorio “secreto”.
Acceder a un directorio a través de URL:
Si escribe picoctf.net/secret/ en su navegador: Si el listado de directorios está activado y no hay un archivo de índice (como index.html), el servidor le mostrará una lista de archivos en la carpeta secreta. Si el listado de directorios está desactivado pero hay un archivo de índice, el servidor mostrará ese archivo y verá una página web.
Visitemos el directorio secreto y veamos qué nos devuelve el servidor web. Vayamos a “…/secret/”.
Continuar hasta “…/secret/hidden/” conduce a una página con otro directorio llamado “superhidden”.
Finalmente, al acceder a la página “superhidden” se revela la bandera
flag: picoCTF{succ3ss_@h3n1c@10n_51b260fe}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Directorios web:
Piense en un servidor web como si fuera un archivador con carpetas (directorios) y archivos. Cada carpeta puede tener más carpetas y archivos dentro. En la terminología web, accedemos a estas carpetas a través de URL (localizadores uniformes de recursos). Cuando accede a website.com/secret/, le está pidiendo al servidor que le muestre el contenido de la carpeta secreta.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias