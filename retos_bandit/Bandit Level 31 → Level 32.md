## Objetivo
There is a git repository at `ssh://bandit31-git@localhost/home/bandit31-git/repo` via the port `2220`. The password for the user `bandit31-git` is the same as for the user `bandit31`.

Clone the repository and find the password for the next level.
## Datos De Acceso al Nivel
```
bandit31
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```
## Solución
```bash
bandit31@bandit:~$ mktemp -d
/tmp/tmp.Q9CKfJYQUY
bandit31@bandit:~$ cd /tmp/tmp.Q9CKfJYQUY
bandit31@bandit:/tmp/tmp.Q9CKfJYQUY$ git clone ssh://bandit31-git@localh
ost:2220/home/bandit31-git/repo
Cloning into 'repo'...
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
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (4/4), done.
bandit31@bandit:/tmp/tmp.Q9CKfJYQUY$ cd repo/
bandit31@bandit:/tmp/tmp.Q9CKfJYQUY/repo$ ls -la
total 20
drwxrwxr-x 3 bandit31 bandit31 4096 Sep  5 04:15 .
drwx------ 3 bandit31 bandit31 4096 Sep  5 04:15 ..
drwxrwxr-x 8 bandit31 bandit31 4096 Sep  5 04:15 .git
-rw-rw-r-- 1 bandit31 bandit31    6 Sep  5 04:15 .gitignore
-rw-rw-r-- 1 bandit31 bandit31  147 Sep  5 04:15 README.md
bandit31@bandit:/tmp/tmp.Q9CKfJYQUY/repo$ cat README.md
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

bandit31@bandit:/tmp/tmp.Q9CKfJYQUY/repo$ echo 'May I come in?' > key.txt
bandit31@bandit:/tmp/tmp.Q9CKfJYQUY/repo$ cat key.txt
May I come in?
bandit31@bandit:/tmp/tmp.Q9CKfJYQUY/repo$ cat .gitignore *.txt
*.txt
May I come in?
bandit31@bandit:/tmp/tmp.Q9CKfJYQUY/repo$ git add -f key.txt
bandit31@bandit:/tmp/tmp.Q9CKfJYQUY/repo$ git commit -m "Contrasena"
[master f84c441] Contrasena
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt
bandit31@bandit:/tmp/tmp.Q9CKfJYQUY/repo$ git push -u origin master
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
Writing objects: 100% (3/3), 323 bytes | 323.00 KiB/s, done.
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

```
## Notas Adicionales

## Referencias
