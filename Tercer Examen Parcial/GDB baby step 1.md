## Descripción 
```
Can you figure out what is in the `eax` register at the end of the `main` function? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`.Disassemble [this](https://artifacts.picoctf.net/c/512/debugger0_a).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
Descarga el binario y ejecuta GDB con el comando `gdb debugger0_a`.  
Desensambla la función `main()` usando `disassemble main` y obtendrás el siguiente volcado:
`0x0000000000001129 <+0>:     endbr64 0x000000000000112d <+4>:     push   %rbp 0x000000000000112e <+5>:     mov    %rsp,%rbp 0x0000000000001131 <+8>:     mov    %edi,-0x4(%rbp) 0x0000000000001134 <+11>:    mov    %rsi,-0x10(%rbp) 0x0000000000001138 <+15>:    mov    $0x86342,%eax 0x000000000000113d <+20>:    pop    %rbp 0x000000000000113e <+21>:    ret`

Como puedes observar, en `<+15>` el valor `0x86342` se almacena en el registro `eax`.  
Recuerda que esta es la sintaxis **AT&T**, por lo que los operandos están invertidos.

So the flag is:
picoCTF{549698}

flag: picoCTF{549698}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias