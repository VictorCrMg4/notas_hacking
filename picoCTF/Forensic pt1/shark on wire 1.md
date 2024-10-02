## Objetivo
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF]
└─$ wireshark capture.pcap &
```
Capturar paquetes.
Tomar un paquete UDP, boton derecho ,follow y avanzar por los streams.

picoCTF{StaT31355_636f6e6e}
## Notas Adicionales
Wireshark es un analizador de red de código abierto ampliamente utilizado que puede capturar y mostrar detalles en tiempo real del tráfico de la red.
## Referencias
