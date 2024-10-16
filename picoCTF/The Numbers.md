## Descripción 
```
The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos$ mkdir crypto
porti_04@DESKTOP-8HT902T:~/pico_retos$ cd crypto
porti_04@DESKTOP-8HT902T:~/pico_retos/crypto$ mkdir thenumbers
porti_04@DESKTOP-8HT902T:~/pico_retos/crypto$ cd thenumbers
porti_04@DESKTOP-8HT902T:~/pico_retos/crypto/thenumbers$ wget https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png
porti_04@DESKTOP-8HT902T:~/pico_retos/crypto/thenumbers$ file the_numbers.png
the_numbers.png: PNG image data, 774 x 433, 8-bit/color RGB, non-interlaced
porti_04@DESKTOP-8HT902T:~/pico_retos/crypto/thenumbers$ eog the-numbers.png

(eog:1270): EOG-WARNING **: 10:27:07.908: Couldn't load icon: Icon 'image-loading' not present in theme Adwaita
porti_04@DESKTOP-8HT902T:~/pico_retos/crypto/thenumbers$

flag: picoCTF{thenumbersmason}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Usamos un alfabeto numerico para sacar la bandera, pues esta incriptada o puedes hacer uso de cyberchef
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias
https://www.springboardstories.co.uk/~mjkizfpy/index.php/topics/codes/2505-alphabet-number
https://gchq.github.io/CyberChef/#input=MTYgOSAzIDE1IDMgMjAgNiB7IDIwIDggNSAxNCAyMSAxMyAyIDUgMTggMTkgMTMgMSAxOSAxNSAxNH0