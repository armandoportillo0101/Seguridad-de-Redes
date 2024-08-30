## Objetivo
The password for the next level is stored in the file **data.txt**, which contains base64 encoded data
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)

## Datos de acceso al nivel
bandit10
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#datos-de-acceso-al-nivel)

## Solución
´´´ 
bandit10@bandit:~$ echo "hola mundo cruel" | base64
aG9sYSBtdW5kbyBjcnVlbAo=
bandit10@bandit:~$ echo "aG9sYSBtdW5kbyBjcnVlbAo=" | base64
YUc5c1lTQnRkVzVrYnlCamNuVmxiQW89Cg==
bandit10@bandit:~$ cat data.txt | base64 -d
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
bandit10@bandit:~$
´´´
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
base64 / es un esquema de codificacion de binario a texto, incluye aZaz09+=/
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias
https://gchq.github.io/CyberChef/