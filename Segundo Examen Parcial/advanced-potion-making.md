## Descripción 
```
Ron just found his own copy of advanced potion making, but its been corrupted by some kind of spell. Help him recover it!

|Challenge Endpoints|
|---|
|Download advanced-potion-making|[advanced-potion-making](https://artifacts.picoctf.net/picoMini+by+redpwn/Forensics/advanced-potion-making/advanced-potion-making)|
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/apm$ wget https://artifacts.picoctf.net/picoMini+by+redpwn/Forensics/advanced-potion-making/advanced-potion-making
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/apm$ file advanced-potion-making
advanced-potion-making: data
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/apm$ xxd advanced-potion-making | less
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/apm$ hexeditor -n advanced-potion-making
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/apm$ eog advanced-potion-making


flag: picoCTF{w1z4rdry}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Arreglé el encabezado de advanced-potion-making , colocando: 89 50 4E 47, abrí la imagen  y ya que me apareció solo un fondo rojo con opción de cambio de color y opción B&N pude leer la bandera.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias