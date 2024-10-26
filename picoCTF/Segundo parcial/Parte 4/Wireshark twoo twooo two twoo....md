## Objetivo
Can you find the flag? [shark2.pcapng](https://mercury.picoctf.net/static/75300327ce3b9f252e9b8911997c8b0a/shark2.pcapng).
## Solución

```bash
┌──(kali㉿kali)-[~/picoCTF/wireshark2]
└─$ wireshark shark2.pcapng 

```

Tras pasar por los streams encontramos un montón de banderas que no son.

Después de buscar en el archivo, noté muchas solicitudes de DNS para varios subdominios de reddshrimpandherring.com

![[Pasted image 20241018220557.png]]

```
1633	9.334169	192.168.38.104	18.217.1.57	DNS	93	Standard query 0xdf26 A cGljb0NU.reddshrimpandherring.com
2042	11.870534	192.168.38.104	18.217.1.57	DNS	93	Standard query 0x3a30 A RntkbnNf.reddshrimpandherring.com
2444	14.503146	192.168.38.104	18.217.1.57	DNS	93	Standard query 0x531d A M3hmMWxf.reddshrimpandherring.com
3140	16.404809	192.168.38.104	18.217.1.57	DNS	93	Standard query 0x99dd A ZnR3X2Rl.reddshrimpandherring.com
3429	18.239530	192.168.38.104	18.217.1.57	DNS	93	Standard query 0x16f6 A YWRiZWVm.reddshrimpandherring.com
3969	20.266171	192.168.38.104	18.217.1.57	DNS	89	Standard query 0xbe68 A fQ==.reddshrimpandherring.com

Eliminamos la demas informacion 

cGljb0NU
RntkbnNf
M3hmMWxf
ZnR3X2Rl
YWRiZWVm
fQ==

cGljb0NURntkbnNfM3hmMWxfZnR3X2RlYWRiZWVmfQ==
```

Lo pasamos a cyber chef con From Base64
![[Pasted image 20241018221100.png]]

*Flag:* picoCTF{dns_3xf1l_ftw_deadbeef}
## Notas Adicionales

## Referencias
https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=DQpjR2xqYjBOVVJudGtibk5mTTNobU1XeGZablIzWDJSbFlXUmlaV1ZtZlE9PQ0K&ieol=CRLF&oeol=CRLF