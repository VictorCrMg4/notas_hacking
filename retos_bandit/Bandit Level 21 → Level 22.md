## Objetivo
A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.
## Datos De Acceso al Nivel
```
bandit21
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
```
## Solución
```bash
bandit21@bandit:~$ ls /etc/cron.d
cronjob_bandit22  cronjob_bandit23  cronjob_bandit24  e2scrub_all  otw-tmp-dir  sysstat
bandit21@bandit:~$ ls -la /etc/cron.d
total 44
drwxr-xr-x   2 root root  4096 Jul 17 15:59 .
drwxr-xr-x 121 root root 12288 Aug  1 14:49 ..
-rw-r--r--   1 root root   120 Jul 17 15:57 cronjob_bandit22
-rw-r--r--   1 root root   122 Jul 17 15:57 cronjob_bandit23
-rw-r--r--   1 root root   120 Jul 17 15:57 cronjob_bandit24
-rw-r--r--   1 root root   201 Apr  8 14:38 e2scrub_all
-rwx------   1 root root    52 Jul 17 15:59 otw-tmp-dir
-rw-r--r--   1 root root   102 Mar 31 00:06 .placeholder
-rw-r--r--   1 root root   396 Jan  9  2024 sysstat
bandit21@bandit:~$ cat /etc/cron.d/
cronjob_bandit22  cronjob_bandit23  cronjob_bandit24  e2scrub_all       otw-tmp-dir       .placeholder      sysstat
bandit21@bandit:~$ cat /etc/cron.d/
cronjob_bandit22  cronjob_bandit23  cronjob_bandit24  e2scrub_all       otw-tmp-dir       .placeholder      sysstat
bandit21@bandit:~$ cat /etc/cron.d/cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```
## Notas Adicionales
cron -  archivo de texto simple que contiene comandos para ejecutarse en un momento específico
/etc/cron.d - ahi ponemos los cronjobs, o dicho de otra forma, los archivos que quiero que se ejecuten cada vez que arranca la computadora
## Referencias
[cron](google.com)
