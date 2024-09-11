## Objetivo
The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)

## Datos de acceso al nivel
bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#datos-de-acceso-al-nivel)

## Solución
```
bandit14@bandit:~$ ls
bandit14@bandit:~$ ls -la
total 24
drwxr-xr-x  3 root root 4096 Jul 17 15:57 .
drwxr-xr-x 70 root root 4096 Jul 17 15:58 ..
-rw-r--r--  1 root root  220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root root 3771 Mar 31 08:41 .bashrc
-rw-r--r--  1 root root  807 Mar 31 08:41 .profile
drwxr-xr-x  2 root root 4096 Jul 17 15:57 .ssh
bandit14@bandit:~$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
bandit14@bandit:~$
bandit14@bandit:~$
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
nc - es una herramienta que permite conectarse a un host remoto, tambien podemos abrir un puerto
nc localhost 3000
	localhost - es el host o la maquina a la que me quiero conectar
	
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias
