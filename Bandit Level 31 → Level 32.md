## Objetivo
There is a git repository at `ssh://bandit31-git@localhost/home/bandit31-git/repo` via the port `2220`. The password for the user `bandit31-git` is the same as for the user `bandit31`.

Clone the repository and find the password for the next level.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)

## Datos de acceso al nivel
bandit31
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#datos-de-acceso-al-nivel)

## Solución
```
bandit31@bandit:/tmp/tmp.wALOMjpCss$ cd repo/
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ ls
README.md
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ cat README.md
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ git branch
* master
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ echo 'May I come in?' > key.txt
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ ls
key.txt  README.md
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ ls -la
total 24
drwxrwxr-x 3 bandit31 bandit31 4096 Sep  7 23:57 .
drwx------ 3 bandit31 bandit31 4096 Sep  7 23:54 ..
drwxrwxr-x 8 bandit31 bandit31 4096 Sep  7 23:55 .git
-rw-rw-r-- 1 bandit31 bandit31    6 Sep  7 23:55 .gitignore
-rw-rw-r-- 1 bandit31 bandit31   15 Sep  7 23:57 key.txt
-rw-rw-r-- 1 bandit31 bandit31  147 Sep  7 23:55 README.md
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ cat .git
cat: .git: Is a directory
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ cat .gitignore
*.txt
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ nano .gitignore
Unable to create directory /home/bandit31/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ cat .gitignore

bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ rm .gitignore
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ git add key.txt
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   key.txt

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    .gitignore

bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ git commit
Unable to create directory /home/bandit31/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

Aborting commit due to empty commit message.
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ git commit -m "Added key.txt"
[master 83a665a] Added key.txt
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$ git push
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit31/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password:
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 2 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 326 bytes | 326.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: ### Attempting to validate files... ####
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
remote: Well done! Here is the password for the next level:
remote: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
To ssh://localhost:2220/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://localhost:2220/home/bandit31-git/repo'
bandit31@bandit:/tmp/tmp.wALOMjpCss/repo$
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
El comando `git commit -m` se utiliza para crear un commit con un mensaje directo.
Este comando guarda los cambios en el historial de Git con el mensaje especificado sin abrir el editor de texto. Es una forma rápida de describir los cambios realizados.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias