## Descripción 
```
How about some hide and seek heh?Download this [file](https://artifacts.picoctf.net/c/371/trace.pcap) and find the flag.
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ wget https://artifacts.picoctf.net/c/371/trace.pcap
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ strings trace.pcap | grep picoCTF{
picoCTF{P64P_4N4L7S1S_SU55355FUL_fc4e803f}3~

flag: picoCTF{P64P_4N4L7S1S_SU55355FUL_fc4e803f}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias