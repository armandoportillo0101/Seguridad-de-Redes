## Descripción 
```
Can you figure out what is in the `eax` register at the end of the `main` function? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`.Debug [this](https://artifacts.picoctf.net/c/520/debugger0_b).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb2$ wget https://artifacts.picoctf.net/c/520/debugger0_b
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb2$ cat debugger0_b


@@@@@�@@@@��@@��  @ @��P.P>@P>@��`.`>@`>@�88@8@ XX@X@DDS�td88@8@ P�td  @ @44Q�tdR�tdP.P>@P>@��/lib64/ld-linux-x86-64.so.2GNU�GNU�� ;�.u���[   ����GNU
                                       ) libc.so.6__libc_start_mainGLIBC_2.2.5__gmon_start__u␦i �?@�?@��H�H��/H��t��H����1�I��^H��H���PTI���@H��P@H��@��/����f.���(@@H=(@@t�H��t      �(@@��f��ff.�@�(@@H��(@@H��H��?H��H�H��t�H��t�(@@���ff.�@���=M/uUH���z����;/]Ð�ff.�@�����UH��}�H�u��E����E�_�E��
�E�E��E��E�;E�|�E�]�f.���AWL�=�,AVI��AUI��ATA��UH�-�,SL)�H�����H��t1��L��L��D��A��H��H9�u�H�[]A\A]A^A_�ff.������H�H��0���LL���`���tL���������zRx
t                                ����/D0����D����=E�C
Dd����eF�I�E �E(�D0�H8�G@n8A0A(B BB�����@�@
�@P>␦X>���o�@�@                            @
8
 h0     ���oH@���o���o@@`>@GCC: (Ubuntu 9.4.0-1ubuntu1~20.04.1) 9.4.0@8@X@|@�@�@@       H@
h@
  @
�@ @ @8 @P>@X>@`>@�?@@@@@(@@��

                              `@
                                �@!
                                   �@7(@@FX>@m
                                              @yP>@������� @���X>@�`>@�P>@� @�@@

�@!@@@M \ @@i @x
                P@e�0@@�
                        P@F
                            @/�(@@�
                                   @=�(@@�
                                          @crtstuff.cderegister_tm_clones__do_global_dtors_auxcompleted.8061__do_global_dtors_aux_fini_array_entryframe_dummy__frame_dummy_init_array_entrydebugger0_b.c__FRAME_END____init_array_end_DYNAMIC__init_array_start__GNU_EH_FRAME_HDR_GLOBAL_OFFSET_TABLE___libc_csu_fini_edata__libc_start_main@@GLIBC_2.2.5__data_start__gmon_start____dso_handle_IO_stdin_used__libc_csu_init_dl_relocate_static_pie__bss_startmain__TMC_END__.symtab.strtab.shstrtab.interp.note.gnu.property.note.gnu.build-id.note.ABI-tag.gnu.hash.dynsym.dynstr.gnu.version.gnu.version_r.rela.dyn.init.text.fini.rodata.eh_frame_hdr.eh_frame.init_array.fini_array.dynamic.got.got.plt.data.bss.comment@#8@86X@X$I|@| W���o�@a
� @ � @ 4�8 @8 �P>�X>�`>@`.��?@�@�@@(@@(0(0+X0�␦*       �5��7   �@�8q���o@@@~���oH@H�h@h�@ @ ���@�


                                                             porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb2$ chmod +x debugger0_b
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb2$ gdb
Display all 7204 possibilities? (y or n)
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb2$ gdb ./debugger0_b
GNU gdb (Ubuntu 12.1-0ubuntu1~22.04.2) 12.1
Copyright (C) 2022 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from ./debugger0_b...
(No debugging symbols found in ./debugger0_b)
(gdb) layout asm
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/gdb2$

picoCTF{30719}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
En gdb  escribí `layout asm`.
Luego, cree un punto de interrupción en main+59 justo después de la última operación con eax para detener el programa después de ese punto.

`b *(main+59)`

Luego, simplemente ejecuté el `run`comando en gdb y el programa se detendrá en el punto de interrupción. En este punto, puede imprimir el registro eax y le proporcionará el valor de eax al final de la función principal.

`print $eax`

Ese número como n alrededor de picoCTF es la bandera.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias