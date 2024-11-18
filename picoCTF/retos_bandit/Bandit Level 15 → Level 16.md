## Objetivo
The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL/TLS encryption.

**Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.**
## Datos De Acceso al Nivel
```
bandit15
Contraseña al nivel:8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```
## Solución
```bash
bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
---
Certificate chain
 0 s:CN = SnakeOil
   i:CN = SnakeOil
   a:PKEY: rsaEncryption, 4096 (bit); sigalg: RSA-SHA256
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
		09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN = SnakeOil
issuer=CN = SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2103 bytes and written 373 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 4096 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: E516BDFCDCA7F596508F9AC1EBB9A871A2CA31CCE52DB06A295DB067B38CBB4E
    Session-ID-ctx:
    Resumption PSK: 70696BE3FC23946ADD894D719EB11AEFDEA016E870EF2B089952C81246E2993EE720A221E09524B1EEC8FAF8C5BB49EE
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 43 87 d0 c4 a5 49 95 26-c8 3e eb 08 d7 47 78 ca   C....I.&.>...Gx.
    0010 - 0d 8d 01 33 ee e8 74 91-2d 4b fb b4 71 f6 b8 8a   ...3..t.-K..q...
    0020 - d9 f9 51 3f 5f bd 02 4e-3d 4d ce 92 3d 91 cb 98   ..Q?_..N=M..=...
    0030 - 48 0f 69 0b ec 47 cd 11-72 9d 0e c7 ef bf 3d aa   H.i..G..r.....=.
    0040 - 57 86 9f d5 e8 6b b8 c3-7e 93 c6 53 73 fc fc be   W....k..~..Ss...
    0050 - 2d 9b 57 8e 76 96 65 2b-13 ad e6 fa 51 64 d2 0f   -.W.v.e+....Qd..
    0060 - 9e 12 95 ba f5 f2 29 32-20 59 d8 81 0c ed 47 06   ......)2 Y....G.
    0070 - b4 3d 8c 50 8f 16 c3 0e-65 4f 7a e6 64 e4 3a 15   .=.P....eOz.d.:.
    0080 - b6 4d e0 e0 f0 5e 1f 93-24 14 1e ca 41 ff e3 e9   .M...^..$...A...
    0090 - 44 62 8f 19 a7 11 8b 2f-2e 2b 9a 78 b4 79 8e b8   Db...../.+.x.y..
    00a0 - d7 9b 76 3a 4d c4 3d 59-29 60 b9 81 c2 50 e2 96   ..v:M.=Y)`...P..
    00b0 - 39 8d 93 21 be 5f fa 40-e3 86 43 66 17 d5 2e a1   9..!._.@..Cf....
    00c0 - 21 b0 d9 79 d4 de b2 0a-21 39 1a 64 e5 31 dd cc   !..y....!9.d.1..
    00d0 - eb fa 2e e6 bb 48 8a b7-51 5a d9 c5 15 02 79 b1   .....H..QZ....y.

    Start Time: 1724868781
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 16A732430B97629B089400C984B04369B086FCA2604EC548498424910C47766A
    Session-ID-ctx:
    Resumption PSK: A35D656860CB284DDB4A50E529D904B85548F82F9D30F138293355D2AD457EF39652CF13D49294DDA9A60FD57D8A4B28
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 43 87 d0 c4 a5 49 95 26-c8 3e eb 08 d7 47 78 ca   C....I.&.>...Gx.
    0010 - 4f 03 5e fb ba ef 14 fd-78 12 72 53 9b 3d 9d af   O.^.....x.rS.=..
    0020 - 87 b5 c7 c4 8b 4b 1b 37-31 1c e2 3c de ca ee 7a   .....K.71..<...z
    0030 - af 3f c9 65 09 e9 36 fe-07 ef be e5 86 14 3b b7   .?.e..6.......;.
    0040 - cf ab 8a 18 23 31 16 d7-08 04 67 bd 9a f1 78 52   ....#1....g...xR
    0050 - 8c 3a b7 d0 43 8c e9 4d-05 d1 b6 80 e4 ba 56 d7   .:..C..M......V.
    0060 - bd 13 9b e4 eb b6 4e 61-b6 43 7e 23 1c 9d 44 07   ......Na.C~#..D.
    0070 - 08 0a 88 ae 9e 79 1a 0f-b3 70 ad ca 1b 79 8b c3   .....y...p...y..
    0080 - fa 3e 21 e2 f5 f5 14 b0-9e a2 99 51 65 17 fd bb   .>!........Qe...
    0090 - 92 48 74 07 40 18 73 c7-dc c9 0e b6 39 a7 f8 51   .Ht.@.s.....9..Q
    00a0 - 2e ee 55 9e d9 04 82 0b-ca 0b 62 a1 4b a2 93 f5   ..U.......b.K...
    00b0 - 10 d9 97 82 1b e2 ee f4-07 39 2b 5a 94 ab 05 7d   .........9+Z...}
    00c0 - ff 5b c6 2f 00 55 7d 86-44 e6 eb 33 f9 b5 c5 95   .[./.U}.D..3....
    00d0 - 62 66 c5 68 3d ea 9d 64-0f 97 01 bc a3 a8 73 60   bf.h=..d......s`

    Start Time: 1724868781
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

closed
bandit15@bandit:~$
```

## Notas Adicionales
- openssl - cliente ssl  se utiliza para gestionar claves privadasy convertir certificados a diferentes formatos
- s_client conecta un cliente ssl a un servidor para verificar la conexion segura y obtener informacion sobre el certificado
## Referencias
- [Secure Socket Layer/Transport Layer Security on Wikipedia](https://en.wikipedia.org/wiki/Transport_Layer_Security)
- [OpenSSL Cookbook - Testing with OpenSSL](https://www.feistyduck.com/library/openssl-cookbook/online/testing-with-openssl/index.html)