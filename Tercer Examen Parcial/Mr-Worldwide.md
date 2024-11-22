## Descripción 
```
A musician left us a [message](https://jupiter.challenges.picoctf.org/static/d5570d48262dbba2a31f2a940409ad9d/message.txt). What's it mean?
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/mrw$ wget https://jupiter.challenges.picoctf.org/static/d5570d48262dbba2a31f2a940409ad9d/message.txt
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/mrw$ cat message.txt
picoCTF{(35.028309, 135.753082)(46.469391, 30.740883)(39.758949, -84.191605)(41.015137, 28.979530)(24.466667, 54.366669)(3.140853, 101.693207)_(9.005401, 38.763611)(-3.989038, -79.203560)(52.377956, 4.897070)(41.085651, -73.858467)(57.790001, -152.407227)(31.205753, 29.924526)}
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/mrw$  nano
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/mrw$ nano solve.py
porti_04@DESKTOP-8HT902T:~/pico_retos/tercer_parcial/mrw$ python3 solve.py
picoCTF{KODIAK_ALASKA}

flag: picoCTF{KODCAK_ALASKA}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Aunque la salida de la consola es `picoCTF{KODCAK_ALASKA}`, la respuesta final es `picoCTF{KODIAK_ALASKA}`la mencionada anteriormente. Sleepy Hollow tiene un `geocode`of `NEWCITY-LCIXI`y un `altgeocode`of `SLEEPYUS-LCIXI`, sin embargo, no había una regla clara sobre cuándo preferir el `altgeocode`sobre el `geocode`, al menos desde una perspectiva programática.

El uso de otros campos como `city`o `region`proporcionó resultados peores.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias