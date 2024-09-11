## Objetivo
There is a git repository at `ssh://bandit29-git@localhost/home/bandit29-git/repo` via the port `2220`. The password for the user `bandit29-git` is the same as for the user `bandit29`.

Clone the repository and find the password for the next level.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)

## Datos de acceso al nivel
bandit29
4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#datos-de-acceso-al-nivel)

## Solución
```
bandit29@bandit:/tmp/tmp.vLcHQg9Fbi/repo$ git log
commit eef534022d1ecc3b41d6de068501c4db4154b2c7 (HEAD -> dev, origin/dev)
Author: Morla Porla <morla@overthewire.org>
Date:   Wed Jul 17 15:57:31 2024 +0000

    add data needed for development

commit 301cf80fd7d0012c519077fcc5e1568cda8e4b8e
Author: Ben Dover <noone@overthewire.org>
Date:   Wed Jul 17 15:57:31 2024 +0000

    add gif2ascii

commit efa5bd803f8335e5e5e9da5c4c7c876aefc9f8b4 (origin/master, origin/HEAD, master)
Author: Ben Dover <noone@overthewire.org>
Date:   Wed Jul 17 15:57:31 2024 +0000

    fix username

commit 5a53eb83a43bac1f0b4e223e469b40ef68a4b6e6
Author: Ben Dover <noone@overthewire.org>
Date:   Wed Jul 17 15:57:31 2024 +0000

    initial commit of README.md
bandit29@bandit:/tmp/tmp.vLcHQg9Fbi/repo$ git checkout dev
Already on 'dev'
Your branch is up to date with 'origin/dev'.
bandit29@bandit:/tmp/tmp.vLcHQg9Fbi/repo$ ls
code  README.md
bandit29@bandit:/tmp/tmp.vLcHQg9Fbi/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL

bandit29@bandit:/tmp/tmp.vLcHQg9Fbi/repo$
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
El comando `git checkout dev` se utiliza para cambiar a la rama llamada `dev`. Si la rama `dev` ya existe en tu repositorio, este comando te moverá a esa rama, actualizando el proyecto a su estado actual.

Si la rama `dev` no existe, Git devolverá un error indicando que la rama no se encontró.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias
https://www.atlassian.com/git/glossary
