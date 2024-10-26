## Descripción 
```
Can you get the flag?

Additional details will be available after launching your challenge instance.
Go to this [website](http://saturn.picoctf.net:53384/) and see what you can discover.
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
Para iniciar el reto debemos hacer clic en “Iniciar instancia. Luego se nos abre una opción que dice “Entra en esta [web](http://saturn.picoctf.net:64960/) y mira lo que puedes descubrir”. Debemos hacer clic en el enlace de la web.
Cuando se abra el sitio web, hacer clic en "Continuar como invitado".
Sabemos que el ejercicio está relacionado con las cookies, así que vamos a comprobarlo. Inspeccionaremos el navegador, iremos a la pestaña de red, haremos clic en recargar. Notaremos que hay una solicitud con un estado de 200, así que la comprobaremos. Haremos clic en ella y luego pasaremos a la pestaña de cookies.
Vemos que hay una cookie llamada "admin" que equivale a 0, así que vamos a cambiarla. Iremos a la pestaña de almacenamiento, haremos clic en la columna "valor" y cambiaremos el 0 a 1.
Actualizaremos la página y obtendremos la bandera


flag: picoCTF{gr4d3_A_c00k13_65fd1e1a}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales

[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias