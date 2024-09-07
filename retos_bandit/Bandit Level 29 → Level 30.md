## Objetivo
There is a git repository at `ssh://bandit29-git@localhost/home/bandit29-git/repo` via the port `2220`. The password for the user `bandit29-git` is the same as for the user `bandit29`.

Clone the repository and find the password for the next level.
## Datos De Acceso al Nivel
```
bandit29
4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
```
## Solución
```bash
bandit29@bandit:~$ mktemp -d
/tmp/tmp.fSTAxC23nW
bandit29@bandit:~$ cd /tmp/tmp.fSTAxC23nW
bandit29@bandit:/tmp/tmp.fSTAxC23nW$ git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit29/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit29/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit29-git@localhost's password:
remote: Enumerating objects: 16, done.
remote: Counting objects: 100% (16/16), done.
remote: Compressing objects: 100% (11/11), done.
Receiving objects: 100% (16/16), done.
remote: Total 16 (delta 2), reused 0 (delta 0), pack-reused 0
Resolving deltas: 100% (2/2), done.
bandit29@bandit:/tmp/tmp.fSTAxC23nW$ ls
repo
bandit29@bandit:/tmp/tmp.fSTAxC23nW$ cd repo/
bandit29@bandit:/tmp/tmp.fSTAxC23nW/repo$ ls
README.md
bandit29@bandit:/tmp/tmp.fSTAxC23nW/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>

bandit29@bandit:/tmp/tmp.fSTAxC23nW/repo$ git branch -a
* master
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
README.md: command not found
bandit29@bandit:/tmp/tmp.fSTAxC23nW/repo$ git checkout dev
branch 'dev' set up to track 'origin/dev'.
Switched to a new branch 'dev'
bandit29@bandit:/tmp/tmp.fSTAxC23nW/repo$ ls -la
total 20
drwxrwxr-x 4 bandit29 bandit29 4096 Sep  5 04:01 .
drwx------ 3 bandit29 bandit29 4096 Sep  5 03:59 ..
drwxrwxr-x 2 bandit29 bandit29 4096 Sep  5 04:01 code
drwxrwxr-x 8 bandit29 bandit29 4096 Sep  5 04:01 .git
-rw-rw-r-- 1 bandit29 bandit29  134 Sep  5 04:01 README.md
bandit29@bandit:/tmp/tmp.fSTAxC23nW/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL

bandit29@bandit:/tmp/tmp.fSTAxC23nW/repo$
```
## Notas Adicionales
Al clonar el repositorio nos movemos a otra rama para ver si ahí se encuentra la contraseña.
## Referencias
