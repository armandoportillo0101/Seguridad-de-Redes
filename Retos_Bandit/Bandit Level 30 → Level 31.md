## Objetivo
There is a git repository at `ssh://bandit30-git@localhost/home/bandit30-git/repo` via the port `2220`. The password for the user `bandit30-git` is the same as for the user `bandit30`.

Clone the repository and find the password for the next level.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#objetivo)

## Datos de acceso al nivel
bandit30
qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#datos-de-acceso-al-nivel)

## Solución
```
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$ ls
branches  config  description  HEAD  hooks  index  info  logs  objects  packed-refs  refs
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$ cat description
Unnamed repository; edit this file 'description' to name the repository.
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$ cat config
[core]
        repositoryformatversion = 0
        filemode = true
        bare = false
        logallrefupdates = true
[remote "origin"]
        url = ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
        fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
        remote = origin
        merge = refs/heads/master
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$ cat index
DIRCf�����f�����C���++��!�L4 ]R?��֛��7w README.mdTREE1 0
��Y.�U����36:F��J�MJ�>Rg�l�`)nĈ�r�^bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$ cat HEAD
ref: refs/heads/master
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$ ls
branches  config  description  HEAD  hooks  index  info  logs  objects  packed-refs  refs
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$ cd info/
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/info$ ls
exclude
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/info$ cat exclude
# git ls-files --others --exclude-from=.git/info/exclude
# Lines that start with '#' are comments.
# For a project mostly in C, the following would be a good set of
# exclude patterns (uncomment them if you want to use them):
# *.[oa]
# *~
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/info$ cd..
cd..: command not found
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/info$ cd ..
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$ cd logs/
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/logs$ cat HEAD
0000000000000000000000000000000000000000 60410f42e05023128098dc1f6991c75e6ae02e47 Ben Dover <noone@overthewire.org> 1725752282 +0000    clone: from ssh://localhost:2220/home/bandit30-git/repo
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/logs$ cd refs/
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/logs/refs$ ls
heads  remotes
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/logs/refs$ cd ..
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/logs$ cd..
cd..: command not found
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/logs$ cd ..
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$  cd ..
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo$ cd.git
cd.git: command not found
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo$ cd .git
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$ ls
branches  config  description  HEAD  hooks  index  info  logs  objects  packed-refs  refs
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$ cd hooks/
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/hooks$ ls
applypatch-msg.sample      pre-applypatch.sample      pre-push.sample          sendemail-validate.sample
commit-msg.sample          pre-commit.sample          pre-rebase.sample        update.sample
fsmonitor-watchman.sample  pre-merge-commit.sample    pre-receive.sample
post-update.sample         prepare-commit-msg.sample  push-to-checkout.sample
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git/hooks$ cd ..
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo/.git$ cd ..
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo$ git tag
secret
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo$ git show secret
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
bandit30@bandit:/tmp/tmp.HFpbbvbGCd/repo$
```
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#soluci%C3%B3n)

## Notas Adicionales
El comando `git tag` se usa para:

1. **Crear una etiqueta**: `git tag nombre-etiqueta`.
2. **Crear una etiqueta con mensaje**: `git tag -a nombre-etiqueta -m "mensaje"`.
3. **Listar etiquetas**: `git tag`.

Se usa para marcar versiones específicas en el historial de commits.
[](https://github.com/armandoportillo0101/Seguridad-de-Redes/blob/main/Plantilla.md#notas-adicionales)

### Referencias
https://www.atlassian.com/git/glossary
