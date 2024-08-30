## Objetivo
The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)

## Datos de acceso al nivel
bandit12
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#datos-de-acceso-al-nivel)

## Solución
```
bandit12@bandit:~$ xxd -r data.txt | file -
/dev/stdin: gzip compressed data, was "data2.bin", last modified: Wed Jul 17 15:57:06 2024, max compression, from Unix
bandit12@bandit:~$ xxd -r data.txt | zcat |file -
/dev/stdin: bzip2 compressed data, block size = 900k
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat |file -
/dev/stdin: gzip compressed data, was "data4.bin", last modified: Wed Jul 17 15:57:06 2024, max compression, from Unix
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat |file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | tar xO | file -
/dev/stdin: bzip2 compressed data, block size = 900k
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | tar xO | bzcat |file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | tar xO | bzcat | tar xO | file -
/dev/stdin: gzip compressed data, was "data9.bin", last modified: Wed Jul 17 15:57:06 2024, max compression, from Unix
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | tar xO | bzcat | tar xO | zcat | file -
/dev/stdin: ASCII text
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | tar xO | bzcat | tar xO | zcat
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
bandit12@bandit:~$
```

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
```
Algunos tipos de compresion en Linux
-----------------------------------------------------
ext comp desc ver en consola
-----------------------------------------------------
.gz gzip gzip -d (gunzip) zcat
.bz2 bzip2 bzip2 -d (bunzip2) bzcat
.tar tar tar xf tar xO
----------------------------------------------------

otros (instalar) :
.zip zip unzip (7z x)
.rar rar unrar (7z x)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias
[SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)