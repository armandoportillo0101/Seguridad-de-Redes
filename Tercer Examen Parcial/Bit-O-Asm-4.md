## Descripción 
```
Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`.Download the assembly dump [here](https://artifacts.picoctf.net/c/511/disassembler-dump0_d.txt).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/b0a4$ wget https://artifacts.picoctf.net/c/511/disassembler-dump0_d.txt
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/b0a4$ cat disassembler-dump0_d.txt
<+0>:     endbr64
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x14],edi
<+11>:    mov    QWORD PTR [rbp-0x20],rsi
<+15>:    mov    DWORD PTR [rbp-0x4],0x9fe1a
<+22>:    cmp    DWORD PTR [rbp-0x4],0x2710
<+29>:    jle    0x55555555514e <main+37>
<+31>:    sub    DWORD PTR [rbp-0x4],0x65
<+35>:    jmp    0x555555555152 <main+41>
<+37>:    add    DWORD PTR [rbp-0x4],0x65
<+41>:    mov    eax,DWORD PTR [rbp-0x4]
<+44>:    pop    rbp
<+45>:    ret

flag: picoCTF{654773}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
```
En un archivo de volcado de ensamblador, se encuentran las siguientes instrucciones:
`<+15>:    mov    DWORD PTR [rbp-0x4],0x9fe1a <+22>:    cmp    DWORD PTR [rbp-0x4],0x2710 <+29>:    jle    0x55555555514e <main+37> <+31>:    sub    DWORD PTR [rbp-0x4],0x65 <+35>:    jmp    0x555555555152 <main+41> <+37>:    add    DWORD PTR [rbp-0x4],0x65 <+41>:    mov    eax,DWORD PTR [rbp-0x4]`

Esto es lo que ejecuta la CPU:

1. **<+15>:** Se almacena `0x9fe1a` en la ubicación de memoria apuntada por `[rbp-0x4]`.
2. **<+22>:** Se compara el valor de `[rbp-0x4]` con `0x2710`.
3. **<+29>:** Si `[rbp-0x4]` es menor o igual a `0x2710`, salta a la instrucción en `<+37>` (pero NO es el caso).
4. **<+31>:** Se resta `0x65` del valor en `[rbp-0x4]` y se almacena el resultado en `[rbp-0x4]`.
5. **<+35>:** Salta a `<+41>`.
6. **<+37>:** [NO EJECUTADA].
7. **<+41>:** El valor almacenado en `[rbp-0x4]` se guarda en el registro `eax`.

Después de todas las operaciones y conversiones desde hexadecimal, obtenemos el número decimal, y nuestra bandera es:  
**picoCTF{654773}**
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias