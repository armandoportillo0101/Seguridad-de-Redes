## Descripción 
```
This image passes LSB statistical analysis, but we can't help but think there must be something to the visual artifacts present in this image...Download the image [here](https://artifacts.picoctf.net/c/303/Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ cd msb
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/msb$ wget https://artifacts.picoctf.net/c/303/Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/msb$ pip install Pillow
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/msb$ wget https://raw.githubusercontent.com/Pulho/sigBits/master/sigBits.py
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/msb$  python3 sigBits.py -t=msb Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png
Done, check the output file!
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/msb$ wget https://raw.githubusercontent.com/Pulho/sigBits/master/sigBits.py
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/msb$  python3 sigBits.py -t=msb Ninja-and-Prince-Genji-
Ukiyoe-Utagawa-Kunisada.flag.png
Done, check the output file!
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/msb$ cat outputSB.txt | grep -o -E "picoCTF.{0,50}
> ^C
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/msb$ cat outputSB.txt | grep -o -E "picoCTF.{0,50}"
picoCTF{........redacted........}"Thou h
picoCTF{15_y0ur_que57_qu1x071c_0r_h3r01c_24d55bee}"Thou h

flag: picoCTF{15_y0ur_que57_qu1x071c_0r_h3r01c_24d55bee}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias