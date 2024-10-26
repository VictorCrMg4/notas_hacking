## Objetivo
The developer of this website mistakenly left an important artifact in the website source, can you find it?The website is [here](http://saturn.picoctf.net:63778/)
## Solución
```bash
┌──(kali㉿kali)-[~]
└─$ httrack http://saturn.picoctf.net:63778/
Mirror launched on Mon, 14 Oct 2024 21:22:32 by HTTrack Website Copier/3.49-5 [XR&CO2014]
mirroring http://saturn.picoctf.net:63778/ with the wizard help..
* saturn.picoctf.net:63778/js/jquery.mCustomScrollbar.concat.min.js (45479 bytes)21/26: saturn.picoctf.net:63778/js/jquery.mCustomScrollbar.concat.min.js (0 bytesDone.: saturn.picoctf.net:63778/images/fevicon.png (153 bytes) - 404
Thanks for using HTTrack!
┌──(kali㉿kali)-[~]
└─$ grep -nr picoCTF
saturn.picoctf.net_63778/css/style.css:328:/** banner_main picoCTF{1nsp3ti0n_0f_w3bpag3s_ec95fa49} **/
grep: .mozilla/firefox/t6hiwr1z.default-esr/sessionstore-backups/recovery.jsonlz4: binary file matches
grep: .mozilla/firefox/t6hiwr1z.default-esr/sessionstore-backups/recovery.baklz4: binary file matches
grep: .mozilla/firefox/t6hiwr1z.default-esr/content-prefs.sqlite: binary file matches
grep: .mozilla/firefox/t6hiwr1z.default-esr/places.sqlite-wal: binary file matches
grep: .mozilla/firefox/t6hiwr1z.default-esr/places.sqlite: binary file matches
.config/wireshark/recent_common:9:recent.capture_file: /home/kali/picoCTF/capture.pcap

```
## Notas Adicionales

## Referencias
