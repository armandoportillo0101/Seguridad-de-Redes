## Descripción 
```
Here's a program that plays rock, paper, scissors against you. I hear something good happens if you win 5 times in a row.The program's source code with the flag redacted can be downloaded [here](https://artifacts.picoctf.net/c/145/game-redacted.c).Connect to the program with netcat:`$ nc saturn.picoctf.net 55009`
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)
## Solución
```
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/RPS$ wget https://artifacts.picoctf.net/c/145/game-redacted.c
porti_04@DESKTOP-8HT902T:~/pico_retos/binexp/RPS$ nc saturn.picoctf.net 55009
Welcome challenger to the game of Rock, Paper, Scissors
For anyone that beats me 5 times in a row, I will offer up a flag I found
Are you ready?
Type '1' to play a game
Type '2' to exit the program
1
1


Please make your selection (rock/paper/scissors):
rockpaperscissors
rockpaperscissors
You played: rockpaperscissors
The computer played: paper
You win! Play again?
Type '1' to play a game
Type '2' to exit the program
1
1


Please make your selection (rock/paper/scissors):
rockpaperscissors
rockpaperscissors
You played: rockpaperscissors
The computer played: scissors
You win! Play again?
Type '1' to play a game
Type '2' to exit the program
1
1


Please make your selection (rock/paper/scissors):
rockpaperscissors
rockpaperscissors
You played: rockpaperscissors
The computer played: paper
You win! Play again?
Type '1' to play a game
Type '2' to exit the program
1
1


Please make your selection (rock/paper/scissors):
rockpaperscissors
rockpaperscissors
You played: rockpaperscissors
The computer played: scissors
You win! Play again?
Type '1' to play a game
Type '2' to exit the program
1
1


Please make your selection (rock/paper/scissors):
rockpaperscissors
rockpaperscissors
You played: rockpaperscissors
The computer played: paper
You win! Play again?
Congrats, here's the flag!
picoCTF{50M3_3X7R3M3_1UCK_58F0F41B}

flag: picoCTF{50M3_3X7R3M3_1UCK_58F0F41B}
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
```
Estas son las partes del código fuente que nos interesan:

// Inicializa las manos y pierde la matriz   
char * hands[ 3 ] = { "piedra" , "papel" , "tijeras" };   
char * loses[ 3 ] = { "papel" , "tijeras" , "piedra" };

// La computadora elige una mano al azar; por ejemplo computer_turn = 0   
int computer_turn = rand () % 3 ;

// Verifica si player_turn contiene la cadena que significa que perdió   
//Por ejemplo -> loses[0] = paper   
  
if ( strstr (player_turn, loses[computer_turn])) {   
    puts ( "¡Ganaste! ¿Juegas de nuevo?" );   
    return  true ;   
  } else {   
    puts ( "Parece que no ganaste esta vez. ¿Juegas de nuevo?" );   
    return  false ;   
  }   
}

Analicemos esto con un ejemplo. Digamos que `int computer_turn = 0`si observamos `hands[0]`, vemos que la computadora eligió "piedra". Ahora, la computadora verificará si la entrada del usuario `player_turn`contiene la cadena que corresponde a `loses[0]`, por ejemplo, "papel".

Sabiendo esto, podemos vencer a la computadora en cada juego si le damos una entrada que contenga todas las cadenas de la `loses`matriz. De esta manera, sin importar qué mano elija la computadora, pensará que el jugador la ha vencido.

Entonces, al darle una entrada `rockpaperscissors`5 veces, ganaremos el juego y obtendremos la bandera
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias