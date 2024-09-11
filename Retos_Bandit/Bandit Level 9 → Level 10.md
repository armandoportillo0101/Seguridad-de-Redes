## Objetivo
The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)

## Datos de acceso al nivel
bandit9
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#datos-de-acceso-al-nivel)

## Solución
bandit9@bandit:~$ ls
data.txt
bandit9@bandit:~$ file data.txt
data.txt: data
bandit9@bandit:~$ strings data.txt | grep ==
\a!;========== the
========== passwordf
========== isc
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
bandit9@bandit:~$
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
strings data.txt | grep == realiza dos acciones principales utilizando dos comandos diferentes, `strings` y `grep`, en conjunto con  `|` para pasar la salida de uno al otro. 

1. **strings data.txt**: Este comando extrae las secuencias de caracteres imprimibles de un archivo binario, en este caso `data.txt`. 
    
2. **|**: El tubo  `|` toma la salida del comando anterior (`strings data.txt`) y la pasa como entrada al siguiente comando.
    
3. grep : grep es un comando que busca patrones dentro de archivos o la salida de otros comandos. En este caso, grep == buscará todas las líneas que contienen el patrón "" en la salida de strings data.txt.
https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales

### Referencias
