## Objetivo
The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:
- human-readable
- 1033 bytes in size
- not executable
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)

## Datos de acceso al nivel
bandit5
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#datos-de-acceso-al-nivel)

## Solución

```
C:\Users\Armando Portillo>ssh bandit5@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit5@bandit.labs.overthewire.org's password:

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * peda (https://github.com/longld/peda.git) in /opt/peda/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ ls -la
total 24
drwxr-xr-x  3 root root    4096 Jul 17 15:57 .
drwxr-xr-x 70 root root    4096 Jul 17 15:58 ..
-rw-r--r--  1 root root     220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root root    3771 Mar 31 08:41 .bashrc
drwxr-x--- 22 root bandit5 4096 Jul 17 15:57 inhere
-rw-r--r--  1 root root     807 Mar 31 08:41 .profile
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
bandit5@bandit:~/inhere$ ls -r
maybehere19  maybehere16  maybehere13  maybehere10  maybehere07  maybehere04  maybehere01
maybehere18  maybehere15  maybehere12  maybehere09  maybehere06  maybehere03  maybehere00
maybehere17  maybehere14  maybehere11  maybehere08  maybehere05  maybehere02
bandit5@bandit:~/inhere$ ls -R
.:
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17

./maybehere00:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere01:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere02:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere03:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere04:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere05:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere06:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere07:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere08:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere09:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere10:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere11:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere12:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere13:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere14:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere15:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere16:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere17:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere18:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

./maybehere19:
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3
bandit5@bandit:~/inhere$ find . -type f -size 1033
bandit5@bandit:~/inhere$ find . -type f -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG








                                        bandit5@bandit:~/inhere$
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)
```
## Notas Adicionales
ls -R  - lista archivos de forma recursiva, es decir, las carpetas con subcarpetas
find . -type f -size 1033c 
	. significa que busca aqui hacia abajo
	-type especifica que busque un archivo del tipo regular
	size 1044c especifica el tamaño de archivo de 1033c
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias