## Objetivo
How about we take you on an adventure on exploring certificate signing requests Take a look at this CSR file [here](https://artifacts.picoctf.net/c/421/readmycert.csr).
## Solución
```bash
┌──(kali㉿kali)-[~/picoCTF/crypto]
└─$ cat readmycert.csr                                     
-----BEGIN CERTIFICATE REQUEST-----
MIICpzCCAY8CAQAwPDEmMCQGA1UEAwwdcGljb0NURntyZWFkX215Y2VydF8zYWE4
MDA5MH0xEjAQBgNVBCkMCWN0ZlBsYXllcjCCASIwDQYJKoZIhvcNAQEBBQADggEP
ADCCAQoCggEBAN1PdpW4sKum7AhFubDl86sflki20dWKkZ/iZBYYX/RYqZIWm9ve
pdfwkeiDdz7KriPzM9tTDuJm1kWv8/3AxHrYwliFHK0lsmUYdOcPfrvlh6SIuZwH
vxhrR0DJ0+W5vU+4j9G/hk2+JLMURh8WZadwBhRcfIxk97OXujjvHS9KplMAs5ul
cSSQcv77QkIcxVg1OSDVZoEjTr131g+/Jox3T+uFPEvzF9iq03JMU39oqfGaFL02
EQTaTl8efLIDkGxrKCc+Jhn4e1mD+9UlUmIn9nsOBCYNrnfq4usAL10ZPMDty2Sx
yVTl0171trvCA9DF5PRG6eMYirJOmF18oSUCAwEAAaAmMCQGCSqGSIb3DQEJDjEX
MBUwEwYDVR0lBAwwCgYIKwYBBQUHAwIwDQYJKoZIhvcNAQELBQADggEBAMa7s/l3
mAwJi7LsosPS6/VlZwfTdiJAv+WOKN9T1q2JRHsAGRrW9Gz5p7nSBKJxevRaOMwn
XWK0HqmN3y2/lor50jWzqLhM4TnbKsakXnEIo90XgHoy+n0DL0296Lg/xoXrRgrh
2o3rtZTc+irqUzTRM7Q1F76LNmgtEXqvbOm6Gx2dASPhVAAfylRBCTyz2dYwg2vM
kwt4e5bTvpze/xyTyI8Pydq09YYJe0+a2cHSgcoyGoWXjIK4CUxjBNXAFxSPCcS3
5JRkBnyGo+KL+XtuK9yCX7xBFkwLybK7Mj4TeGiwDsR/0SwqyWGb7Q2m58ay8RVm
pmAIEs21M3236Z4=
-----END CERTIFICATE REQUEST-----

┌──(kali㉿kali)-[~/picoCTF/crypto]
└─$ openssl req -in readmycert.csr -text
Certificate Request:
    Data:
        Version: 1 (0x0)
        Subject: CN=picoCTF{read_mycert_3aa80090}, name=ctfPlayer
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                Public-Key: (2048 bit)
                Modulus:
                    00:dd:4f:76:95:b8:b0:ab:a6:ec:08:45:b9:b0:e5:
                    f3:ab:1f:96:48:b6:d1:d5:8a:91:9f:e2:64:16:18:
                    5f:f4:58:a9:92:16:9b:db:de:a5:d7:f0:91:e8:83:
                    77:3e:ca:ae:23:f3:33:db:53:0e:e2:66:d6:45:af:
                    f3:fd:c0:c4:7a:d8:c2:58:85:1c:ad:25:b2:65:18:
                    74:e7:0f:7e:bb:e5:87:a4:88:b9:9c:07:bf:18:6b:
                    47:40:c9:d3:e5:b9:bd:4f:b8:8f:d1:bf:86:4d:be:
                    24:b3:14:46:1f:16:65:a7:70:06:14:5c:7c:8c:64:
                    f7:b3:97:ba:38:ef:1d:2f:4a:a6:53:00:b3:9b:a5:
                    71:24:90:72:fe:fb:42:42:1c:c5:58:35:39:20:d5:
                    66:81:23:4e:bd:77:d6:0f:bf:26:8c:77:4f:eb:85:
                    3c:4b:f3:17:d8:aa:d3:72:4c:53:7f:68:a9:f1:9a:
                    14:bd:36:11:04:da:4e:5f:1e:7c:b2:03:90:6c:6b:
                    28:27:3e:26:19:f8:7b:59:83:fb:d5:25:52:62:27:
                    f6:7b:0e:04:26:0d:ae:77:ea:e2:eb:00:2f:5d:19:
                    3c:c0:ed:cb:64:b1:c9:54:e5:d3:5e:f5:b6:bb:c2:
                    03:d0:c5:e4:f4:46:e9:e3:18:8a:b2:4e:98:5d:7c:
                    a1:25
                Exponent: 65537 (0x10001)
        Attributes:
            Requested Extensions:
                X509v3 Extended Key Usage: 
                    TLS Web Client Authentication
    Signature Algorithm: sha256WithRSAEncryption
    Signature Value:
        c6:bb:b3:f9:77:98:0c:09:8b:b2:ec:a2:c3:d2:eb:f5:65:67:
        07:d3:76:22:40:bf:e5:8e:28:df:53:d6:ad:89:44:7b:00:19:
        1a:d6:f4:6c:f9:a7:b9:d2:04:a2:71:7a:f4:5a:38:cc:27:5d:
        62:b4:1e:a9:8d:df:2d:bf:96:8a:f9:d2:35:b3:a8:b8:4c:e1:
        39:db:2a:c6:a4:5e:71:08:a3:dd:17:80:7a:32:fa:7d:03:2f:
        4d:bd:e8:b8:3f:c6:85:eb:46:0a:e1:da:8d:eb:b5:94:dc:fa:
        2a:ea:53:34:d1:33:b4:35:17:be:8b:36:68:2d:11:7a:af:6c:
        e9:ba:1b:1d:9d:01:23:e1:54:00:1f:ca:54:41:09:3c:b3:d9:
        d6:30:83:6b:cc:93:0b:78:7b:96:d3:be:9c:de:ff:1c:93:c8:
        8f:0f:c9:da:b4:f5:86:09:7b:4f:9a:d9:c1:d2:81:ca:32:1a:
        85:97:8c:82:b8:09:4c:63:04:d5:c0:17:14:8f:09:c4:b7:e4:
        94:64:06:7c:86:a3:e2:8b:f9:7b:6e:2b:dc:82:5f:bc:41:16:
        4c:0b:c9:b2:bb:32:3e:13:78:68:b0:0e:c4:7f:d1:2c:2a:c9:
        61:9b:ed:0d:a6:e7:c6:b2:f1:15:66:a6:60:08:12:cd:b5:33:
        7d:b7:e9:9e
-----BEGIN CERTIFICATE REQUEST-----
MIICpzCCAY8CAQAwPDEmMCQGA1UEAwwdcGljb0NURntyZWFkX215Y2VydF8zYWE4
MDA5MH0xEjAQBgNVBCkMCWN0ZlBsYXllcjCCASIwDQYJKoZIhvcNAQEBBQADggEP
ADCCAQoCggEBAN1PdpW4sKum7AhFubDl86sflki20dWKkZ/iZBYYX/RYqZIWm9ve
pdfwkeiDdz7KriPzM9tTDuJm1kWv8/3AxHrYwliFHK0lsmUYdOcPfrvlh6SIuZwH
vxhrR0DJ0+W5vU+4j9G/hk2+JLMURh8WZadwBhRcfIxk97OXujjvHS9KplMAs5ul
cSSQcv77QkIcxVg1OSDVZoEjTr131g+/Jox3T+uFPEvzF9iq03JMU39oqfGaFL02
EQTaTl8efLIDkGxrKCc+Jhn4e1mD+9UlUmIn9nsOBCYNrnfq4usAL10ZPMDty2Sx
yVTl0171trvCA9DF5PRG6eMYirJOmF18oSUCAwEAAaAmMCQGCSqGSIb3DQEJDjEX
MBUwEwYDVR0lBAwwCgYIKwYBBQUHAwIwDQYJKoZIhvcNAQELBQADggEBAMa7s/l3
mAwJi7LsosPS6/VlZwfTdiJAv+WOKN9T1q2JRHsAGRrW9Gz5p7nSBKJxevRaOMwn
XWK0HqmN3y2/lor50jWzqLhM4TnbKsakXnEIo90XgHoy+n0DL0296Lg/xoXrRgrh
2o3rtZTc+irqUzTRM7Q1F76LNmgtEXqvbOm6Gx2dASPhVAAfylRBCTyz2dYwg2vM
kwt4e5bTvpze/xyTyI8Pydq09YYJe0+a2cHSgcoyGoWXjIK4CUxjBNXAFxSPCcS3
5JRkBnyGo+KL+XtuK9yCX7xBFkwLybK7Mj4TeGiwDsR/0SwqyWGb7Q2m58ay8RVm
pmAIEs21M3236Z4=
-----END CERTIFICATE REQUEST-----


```
## Notas Adicionales

## Referencias
