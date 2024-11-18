## Objetivo
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

**NOTE:** Try connecting to your own network daemon to see if it works as you think
## Datos De Acceso al Nivel
```
bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```
## Solución
```bash
bandit20@bandit:~$ nc -lnvp localhost:5050
nc: getaddrinfo: Servname not supported for ai_socktype
bandit20@bandit:~$ nc -lnvp localhost 5050
usage: nc [-46CDdFhklNnrStUuvZz] [-I length] [-i interval] [-M ttl]
          [-m minttl] [-O length] [-P proxy_username] [-p source_port]
          [-q seconds] [-s sourceaddr] [-T keyword] [-V rtable] [-W recvlimit]
          [-w timeout] [-X proxy_protocol] [-x proxy_address[:port]]
          [destination] [port]
bandit20@bandit:~$ nc  localhost 5050
bandit20@bandit:~$ nc localhost 5050
bandit20@bandit:~$ nc -lvnp 6666 <<<0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO &
[1] 3136756
bandit20@bandit:~$ Listening on 0.0.0.0 6666
./suconnect 6666
Connection received on 127.0.0.1 37752
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
[1]+  Done                    nc -lvnp 6666 <<< 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
bandit20@bandit:~$
```
## Notas Adicionales
&  -- envia una tarea al segundo plano
fg - sacar una tarea del segundo plano
## Referencias
