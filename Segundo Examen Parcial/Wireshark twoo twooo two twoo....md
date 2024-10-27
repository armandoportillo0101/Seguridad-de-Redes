## Descripción 
```
Can you find the flag? [shark2.pcapng](https://mercury.picoctf.net/static/0fe13a33318e756f71c35cb490e64c81/shark2.pcapng).
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
1. Tras una inspección inicial, parece haber muchas solicitudes a un `/flag`punto final. Cada solicitud muestra una bandera diferente, por lo que deben ser una distracción.
    
2. Después de buscar en el archivo, noté muchas solicitudes de DNS para varios subdominios de `reddshrimpandherring.com`. Parece que se trata del tráfico sospechoso al que se refiere una de las sugerencias del desafío.
    
3. Muchas de las consultas DNS tienen como destino 8.8.8.8. Sin embargo, un subconjunto tiene como destino 18.217.1.57.
    
4. Podemos aplicar el filtro `dns and ip.dst==18.217.1.57`para ver únicamente las solicitudes DNS dirigidas a esta dirección IP. Si tomamos los subdominios de `reddshrimpandherring.com`y los agregamos en orden obtenemos:`cGljb0NURntkbnNfM3hmMWxfZnR3X2RlYWRiZWVmfQ==`
    
5. Al decodificar la cadena anterior como base64 obtenemos la bandera.
    
6. Alternativamente, este archivo se puede analizar utilizando [apackets.com](https://apackets.com/) . Simplemente cargue el archivo, vaya a la página DNS y desplácese hacia abajo para ver las solicitudes ordenadas.

flag: picoCTF{dns_3xf1l_ftw_deadbeef}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias