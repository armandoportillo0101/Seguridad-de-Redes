## Objetivo
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)

## Datos de acceso al nivel
bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#datos-de-acceso-al-nivel)

## Solución
```
bandit20@bandit:~$ nc -lnvp 6666 <<< "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO"
Listening on 0.0.0.0 6666
^C
bandit20@bandit:~$ nc -lnvp 3445 <<< 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO &
[1] 3139901
bandit20@bandit:~$ Listening on 0.0.0.0 3445
^C
bandit20@bandit:~$ jobs
[1]+  Running                 nc -lnvp 3445 <<< 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO &
bandit20@bandit:~$ ls -la
total 36
drwxr-xr-x  2 root     root      4096 Jul 17 15:57 .
drwxr-xr-x 70 root     root      4096 Jul 17 15:58 ..
-rw-r--r--  1 root     root       220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root     root      3771 Mar 31 08:41 .bashrc
-rw-r--r--  1 root     root       807 Mar 31 08:41 .profile
-rwsr-x---  1 bandit21 bandit20 15604 Jul 17 15:57 suconnect
bandit20@bandit:~$ ./suconnect 3445
Connection received on 127.0.0.1 59286
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
[1]+  Done                    nc -lnvp 3445 <<< 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
bandit20@bandit:~$
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
& si agregamos un simbolo  de estos al final de un comando, lo estamos enviando al segundo plano (background)
jobs me muestra que comandos estan en segundo plano
fg saca un proceso o comando del segundo plano y lo trae al primer plano (foreground)
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias
