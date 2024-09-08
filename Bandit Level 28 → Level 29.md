## Objetivo
There is a git repository at `ssh://bandit28-git@localhost/home/bandit28-git/repo` via the port `2220`. The password for the user `bandit28-git` is the same as for the user `bandit28`.

Clone the repository and find the password for the next level.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)

## Datos de acceso al nivel
bandit28
Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#datos-de-acceso-al-nivel)

## Solución
```
bandit28@bandit:/tmp/tmp.Pb2XZhoREx/repo$ git log
commit 73f5d0435070c8922da12177dc93f40b2285e22a (HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Wed Jul 17 15:57:30 2024 +0000

    add missing data

commit 5f7265568c7b503b276ec20f677b68c92b43b712
Author: Ben Dover <noone@overthewire.org>
Date:   Wed Jul 17 15:57:30 2024 +0000

    initial commit of README.md
bandit28@bandit:/tmp/tmp.Pb2XZhoREx/repo$ git checkout 73f5d0435070c8922da12177dc93f40b2285e22a
HEAD is now at 73f5d04 add missing data
bandit28@bandit:/tmp/tmp.Pb2XZhoREx/repo$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7

bandit28@bandit:/tmp/tmp.Pb2XZhoREx/repo$

```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
El comando `git checkout` se usa para:

1. **Cambiar de rama**: `git checkout nombre-rama`.
2. **Crear y cambiar a una nueva rama**: `git checkout -b nueva-rama`.
3. **Restaurar archivos** a un estado anterior: `git checkout commit archivo`.

Es una herramienta flexible para navegar entre ramas y revertir cambios en Gi
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias