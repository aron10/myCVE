### 

### Source code

[Best salon management system project in php](https://www.sourcecodester.com/php/18171/best-salon-management-system-project-php.htmlhttps://www.sourcecodester.com/php/18171/best-salon-management-system-project-php.html)

### 

### Description

SQL Injection vulnerability in sourcecodester Best salon management system project in php, A vulnerability has been found that is rated as high risk, affecting some unknown functionality of the panel\index.php file, Using parameter 'username' to construct malicious SQL statements to obtain sensitive information, thus causing harm

### 

### Analysis vulnerability

```
panel\index.php
```

By reviewing the code segment,, the user input `$_POST['username']` is concatenated into the SQL query statement, which is obviously susceptible to SQL injection attacks

![1 login page.png](assets/2%20code.png)


### Recurrent vulnerability

进入到后台登录页 http://website/panel/

![image-20241023160251059](assets/1%20login%20page.png)

Submit the input content

Save the packet and use sqlmap attack，Add a symbol "*" after the "username=2" in line 15.

![1 login page.png](assets/3%20post%20msg.png)

```
Open the Kali Linux，Open Terminal Heler ,input：
sqlmap  -r data.txt --current-db
```

![1 login page.png](/Users/yaolin/Downloads/src挖掘/CVE-2025-barbar/assets/4%20database.png)

This data packet did not include an authentication value, meaning no identity verification was performed. Therefore, it was possible to launch an attack remotely without logging in.
Additionally, this attack packet employed two injection methods: time-based blind injection and UNION query, and successfully injected into the database name.