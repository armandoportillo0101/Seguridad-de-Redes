## Descripción 
```
Someone might have hidden the password in the trace file.Find the key to unlock [this file](https://artifacts.picoctf.net/c/494/flag.zip). [This tracefile](https://artifacts.picoctf.net/c/494/dump.pcap) might be good to analyze.
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ wget https://artifacts.picoctf.net/c/494/flag.zip
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ wget https://artifacts.picoctf.net/c/494/dump.pcap
--2024-10-26 15:48:40--  https://artifacts.picoctf.net/c/494/dump.pcap
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ unzip flag.zip
Archive:  flag.zip
[flag.zip] flag password:
password incorrect--reenter:
   skipping: flag                    incorrect password
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ wireshark dump.pcap
 ** (wireshark:8258) 15:50:14.821753 [GUI WARNING] -- QStandardPaths: wrong permissions on runtime directory /run/user/1000/, 0755 instead of 0700
nl80211 not found.
^C
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ echo -n iBwaWNvQ1RGe1 | base64 -di
�␦X����base64: invalid input
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ echo -n iBwaWNvQ1RGe1aaa | base64 -di
�␦X����զ�porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ echo -n iBwaWNvQ1RGe1aaaaaaa | baecho -n iBwaWNvQ1RGe1aaaaaaa | base64 -di
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ echo -n iBwaWNvQ1RGe1aaaaaaaaaaa | base64 -di
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ echo -n iBwaWNvQ1RGe1aaaaaaaaaaaaaaaa | base64 -diaa | base64 -di
�␦X����զ�i��i��i��base64: invalid input
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ echo -n aaaiBwaWNvQ1RGe1 | base64 -di
i���6�5Dg�porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ echo -n aaaaaaaiBwaWNvQ1RGe1 | becho -n aaaaaaaiBwaWNvQ1RGe1 | base64 -di
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ echo -n aaaaaaaaaaaiBwaWNvQ1RGe1 | base64 -di | base64 -di
i��i��i���6�5Dg�porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial echo -n iBwaWNvQ1RGe1aaaaa== | base64 -di
�␦X����զ�iporti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ echo -n aiBwaWNvQ1RGe1== | base6echo -n aiBwaWNvQ1RGe1== | base64 -di
j picoCTF{porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ unzip -P picoCTF{ flag.zip
Archive:  flag.zip
   skipping: flag                    incorrect password
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ echo -n aaAABBHHPJGTFRLKVGhpcyBpcyB0aGUgc2VjcmV0OiBwaWNvQ1RGe1IzNERJTkdfTE9LZF8= | base64 -di
i��<���This is the secret: picoCTF{R34DING_LOKd_porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ unzip -P picoCTF{R34DING_LOKd_ flag.zip
Archive:  flag.zip
 extracting: flag
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/findandopen$ cat flag
picoCTF{R34DING_LOKd_fil56_succ3ss_b98dda6a}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Use wireshark 
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias
https://medium.com/@12gnathic.xsgb9/picoctf-2023-findandopen-writeup-e8911048a54d