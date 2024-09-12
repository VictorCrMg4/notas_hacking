## Objetivo
I accidentally wrote the flag down. Good thing I deleted it!You download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/77/challenge.zip)
## Solución
```bash
victormcm-picoctf@webshell:~$ ls
challenge.zip  drop-in
victormcm-picoctf@webshell:~$ cd drop-in/
victormcm-picoctf@webshell:~/drop-in$ ls
message.txt
victormcm-picoctf@webshell:~/drop-in$ git log

victormcm-picoctf@webshell:~/drop-in$ git commit 3d5ec8a26ee7b092a1760fea18f384c35e435139
error: pathspec '3d5ec8a26ee7b092a1760fea18f384c35e435139' did not match any file(s) known to git
victormcm-picoctf@webshell:~/drop-in$ git checkout 3d5ec8a26ee7b092a1760fea18f384c35e435139
Note: switching to '3d5ec8a26ee7b092a1760fea18f384c35e435139'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 3d5ec8a create flag

victormcm-picoctf@webshell:~/drop-in$ git branch -a
victormcm-picoctf@webshell:~/drop-in$ git log
victormcm-picoctf@webshell:~/drop-in$ git checkout 3d5ec8a26ee7b092a1760fea18f384c35e435139
HEAD is now at 3d5ec8a create flag
victormcm-picoctf@webshell:~/drop-in$ ls
message.txt
victormcm-picoctf@webshell:~/drop-in$ cat message.txt 
picoCTF{s@n1t1z3_30e86d36}
victormcm-picoctf@webshell:~/drop-in$ 
```
## Notas Adicionales
Con git checkout puedes regresarte a un commit
## Referencias