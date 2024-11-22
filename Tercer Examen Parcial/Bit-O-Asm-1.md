## Descripción 
```
Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`.Download the assembly dump [here](https://artifacts.picoctf.net/c/509/disassembler-dump0_a.txt).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/b0a1$ wget https://artifacts.picoctf.net/c/509/disassembler-dump0_a.txt
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/b0a1$ cat disassembler-dump0_a.txt
<+0>:     endbr64
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x4],edi
<+11>:    mov    QWORD PTR [rbp-0x10],rsi
<+15>:    mov    eax,0x30
<+20>:    pop    rbp
<+21>:    ret
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/b0a1$ python3
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print("{:d}".format(0x30))  # Imprime 48 en decimal
48

flag: picoCTF{48}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Según el contenido del asm y la descripción, el contenido del registro eax es 0x30.
Para convertir este valor hexadecimal a decimal, puedes utilizar una herramienta en línea o varios métodos en la línea de comandos. Inicialmente, utilicé el método printf.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias