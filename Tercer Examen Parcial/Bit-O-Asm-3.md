## Descripción 
```
Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`.Download the assembly dump [here](https://artifacts.picoctf.net/c/530/disassembler-dump0_c.txt).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/b0a3$ wget https://artifacts.picoctf.net/c/530/disassembler-dump0_c.txt
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/b0a3$ cat disassembler-dump0_c.txt
<+0>:     endbr64
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x14],edi
<+11>:    mov    QWORD PTR [rbp-0x20],rsi
<+15>:    mov    DWORD PTR [rbp-0xc],0x9fe1a
<+22>:    mov    DWORD PTR [rbp-0x8],0x4
<+29>:    mov    eax,DWORD PTR [rbp-0xc]
<+32>:    imul   eax,DWORD PTR [rbp-0x8]
<+36>:    add    eax,0x1f5
<+41>:    mov    DWORD PTR [rbp-0x4],eax
<+44>:    mov    eax,DWORD PTR [rbp-0x4]
<+47>:    pop    rbp
<+48>:    ret
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer

flag: picoCTF{2619997}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
En un archivo de volcado de ensamblador, se encuentran las siguientes instrucciones

`<+15>:    mov    DWORD PTR [rbp-0xc],0x9fe1a <+22>:    mov    DWORD PTR [rbp-0x8],0x4 <+29>:    mov    eax,DWORD PTR [rbp-0xc] <+32>:    imul   eax,DWORD PTR [rbp-0x8] <+36>:    add    eax,0x1f5 <+41>:    mov    DWORD PTR [rbp-0x4],eax <+44>:    mov    eax,DWORD PTR [rbp-0x4]`

Esto es lo que ejecuta la CPU:

1. **<+15>:** Se almacena el valor DWORD `654874` en la ubicación de memoria apuntada por `[rbp-0xc]`.
2. **<+22>:** Se almacena el valor DWORD `4` en la ubicación de memoria apuntada por `[rbp-0x8]`.
3. **<+29>:** El valor almacenado en la ubicación de memoria apuntada por `[rbp-0xc]` (`654874`) se almacena en el registro `eax`.
4. **<+32>:** El valor almacenado en el registro `eax` se multiplica por el valor almacenado en la ubicación de memoria apuntada por `[rbp-0x8]` (`4`), y el resultado se almacena en el registro `eax`.
5. **<+36>:** Se suma `501` al valor almacenado en el registro `eax`, y el resultado se almacena nuevamente en el registro `eax`.
6. **<+41>:** El valor almacenado en el registro `eax` se guarda en la ubicación de memoria apuntada por `[rbp-0x4]`.
7. **<+44>:** El valor de la ubicación de memoria apuntada por `[rbp-0x4]` se almacena en el registro `eax`.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias