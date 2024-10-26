## Descripción 
```
The developer of this website mistakenly left an important artifact in the website source, can you find it?

Additional details will be available after launching your challenge instance.
The website is [here](http://saturn.picoctf.net:59236/)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```bash 
porti_04@DESKTOP-8HT902T:~/pico_retos$ cd  examen_parcial_2
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ nc http://saturn.picoctf.net:59236/
nc: missing port number
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ wget -mpEk http://saturn.picoctf.net:59236/
--2024-10-21 16:04:23--  http://saturn.picoctf.net:59236/
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ grep -r 'picoCTF{'
saturn.picoctf.net:59236/css/style.css:/** banner_main picoCTF{1nsp3ti0n_0f_w3bpag3s_587d12b8} **/

flag: picoCTF{1nsp3ti0n_0f_w3bpag3s_587d12b8}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Cuando abrimos el enlace, comenzamos a mirar el código fuente, pero rápidamente vemos que hay muchísimos archivos de código fuente diferentes que llevaría una eternidad revisarlos.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias