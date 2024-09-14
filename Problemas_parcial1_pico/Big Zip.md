## Objetivo
Unzip this archive and find the flag.

## Solución
```
porti_04@DESKTOP-8HT902T:~/big-zip-files$ cd ..
porti_04@DESKTOP-8HT902T:~$ grep -r big-zip-files -e pico
big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
porti_04@DESKTOP-8HT902T:~$
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
- **grep**: Es una herramienta de búsqueda en Linux que busca patrones de texto en archivos o la salida de otros comandos.
    
- **-r**: Esta opción indica a `grep` que realice una búsqueda recursiva en subdirectorios. Esto significa que buscará en todos los archivos y directorios dentro de `big-zip-files`.
    
- **big-zip-files**: Es el directorio (o archivo) en el que `grep` buscará los patrones especificados.
    
- **-e pico**: Esta opción permite especificar el patrón que `grep` buscará. En este caso, `pico` es el patrón que `grep` buscará en los archivos dentro de `big-zip-files`.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias