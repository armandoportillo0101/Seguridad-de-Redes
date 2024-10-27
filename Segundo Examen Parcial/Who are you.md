## Descripción 
```
Let me in. Let me iiiiiiinnnnnnnnnnnnnnnnnnnn [http://mercury.picoctf.net:36622/](http://mercury.picoctf.net:36622/)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ curl http://mercury.picoctf.net:36622/ | grep "<h3.*>.*<\/h3>"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1073  100  1073    0     0   3817      0 --:--:-- --:--:-- --:--:--  3845
                                <h3 style="color:red">Only people who use the official PicoBrowser are allowed on this site!</h3>
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ curl --user-agent "picobrowser"  http://mercury.picoctf.net:36622/ | grep "<h3.*>.*<\/h3>"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1054  100  1054    0     0   2996      0 --:--:-- --:--:-- --:--:--  2994
                                <h3 style="color:red">I don&#39;t trust users visiting from another site.</h3
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ curl --user-agent "picobrowser" --referer  "http://mercury.picoctf.net:36622/"  http://mercury.picoctf.net:36622/ | grep "<h3.*>.*<\/h3>"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1040  100  1040    0     0   4586      0 --:--:-- --:--:-- --:--:--  4581
                                <h3 style="color:red">Sorry, this site only worked in 2018.</h3>
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ curl --user-agent "picobrowser" --referer "http://mercury.picoctf.net:36622/" -H "Date: Mon, 23 11 2018 23:23:23 GMT" http://mercury.picoctf.net:36622/ | grep "<h3.*>.*<\/h3>"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1046  100  1046    0     0   4448      0 --:--:-- --:--:-- --:--:--  4470
                                <h3 style="color:red">I don&#39;t trust users who can be tracked.</h3>
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ curl --user-agent "picobrowser" --referer "http://mercury.picoctf.net:36622/" -H "Date: Mon, 23 11 2018 23:23:23 GMT" -H "DNT: 1"  http://mercury.picoctf.net:36622/| grep "<h3.*>.*<\/h3>"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1047  100  1047    0     0   4522      0 --:--:-- --:--:-- --:--:--  4532
                                <h3 style="color:red">This website is only for people from Sweden.</h3>
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ curl --user-agent "picobrowser" --referer "http://mercury.picoctf.net:36622/"  -H "Date: Mon, 23 11 2018 23:23:23 GMT" -H "DNT: 1" -H "X-Forwarded-For: 2.71.255.255"  http://mercury.picoctf.net:36622/  | grep "<h3.*>.*<\/h3>"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1056  100  1056    0     0   3525      0 --:--:-- --:--:-- --:--:--  3520
                                <h3 style="color:red">You&#39;re in Sweden but you don&#39;t speak Swedish?</h3>
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ curl --user-agent "picobrowser" --referer  "http://mercury.picoctf.net:36622/" -H "Date: Mon, 23 11 2018 23:23:23 GMT" -H "DNT: 1" -H "X-Forwarded-For: 2.71.255.255" -H "Accept-Language: sv-SE"  http://mercury.picoctf.net:36622/ | grep "<h3.*>.*<\/h3>"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1062  100  1062    0     0   3978      0 --:--:-- --:--:-- --:--:--  3992
                                <h3 style="color:green">What can I say except, you are welcome</h3>
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2$ curl --user-agent "picobrowser" --referer  "http://mercury.picoctf.net:36622/" -H "Date: Mon, 23 11 2018 23:23:23 GMT" -H "DNT: 1" -H "X-Forwarded-For: 2.71.255.255" -H "Accept-Language: sv-SE"  http://mercury.picoctf.net:36622/ | grep "<b>.*</b>"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1062  100  1062    0     0    885      0  0:00:01  0:00:01 --:--:--   885
                        <b>picoCTF{http_h34d3rs_v3ry_c0Ol_much_w0w_0da16bb2}</b>

flag: picoCTF{http_h34d3rs_v3ry_c0Ol_much_w0w_0da16bb2}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias