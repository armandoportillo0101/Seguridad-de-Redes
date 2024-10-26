## Descripción 
```
Download the packet capture file and use packet analysis software to find the flag.

- [Download packet capture](https://artifacts.picoctf.net/c/196/network-dump.flag.pcap)
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/packetsp$ wget https://artifacts.picoctf.net/c/196/network-dump.flag.pcap
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/packetsp$ wireshark network-dump.flag.pcap
 ** (wireshark:13859) 16:14:10.065455 [GUI WARNING] -- QStandardPaths: wrong permissions on runtime directory /run/user/1000/, 0755 instead of 0700
nl80211 not found.
^C
porti_04@DESKTOP-8HT902T:~/pico_retos/examen_parcial_2/packetsp$ strings network-dump.flag.pcap | tr -d ' ' | grep -oE "picoCTF{.*}"
picoCTF{p4ck37_5h4rk_01b0a0d6}

flag: picoCTF{p4ck37_5h4rk_01b0a0d6}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
Al abrirlo con Wireshark, notamos que solo hay 9 paquetes y solo una conversación en TCP, que de hecho es la bandera.
Sin embargo, dado que la bandera está presente abiertamente en los bytes del paquete, podemos usar `strings`para obtener la bandera.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias