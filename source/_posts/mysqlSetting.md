---
title: "[MySQL] Setting"
date: 2018-02-26 10:47:33
categories:
	- Develop
tags:
	- MySQL
	- Database
---

Mysql 的一些常用設定及指令

<!-- more -->

## 重啟
使用` command line`
``` bash
net stop mysql
net start mysql
```
![](mysql-restart.png)

使用` 服務`
1. ` win` + ` R` 輸入 ` services.msc` 開啟服務
2. 找到 ` MySQL` 右鍵 ` 重新啟動`
![](cmd-services.png)
![](services-mysql-restart.png)
***
## 字集Character

打開 ` my.ini` *(通常在 \MySQL\MySQL Server x.x\ 下 [x.x 為版本])*

將所有` default-character-set=Latin1` 改成` default-character-set=utf8`
![](my-ini-char.png)

使用` command line` 檢查字集是否都改成` utf8`
``` bash
mysql -u<User> -p<Password>
show variables like '%char%';
```
> -p連著密碼中間不空白：密碼將自動填入，不用再輸入一次

![](mysql-char.png)

***
## 紀錄Log

在` my.ini` 最下面加入
```
[mysqld]
...設定...
```

1. Query Log (Select, Insert, Update, Delete)
> 記錄所有SQL
```
[mysqld]
general_log_file = "<backup output path>/sql.log"
general_log = 1
```

2. Slow SQL Log
> 記錄超過時間的SQL
```
[mysqld]
slow-query-log
slow_query_log_file = "<backup output path>/slow_sql.log"
# 設定query時間(秒為單位)
long_query_time = 1
log-long-format
```

3. Error Log
> 記錄錯誤SQL
```
[mysqld]
log_error= "<backup output path>/error.log"
```

***
## 匯入匯出

1. 匯出
``` bash
cd <output folder>
mysqldump -u<User> -p<Password> <database> --routines > backup.sql
```

2. 匯入
``` bash
cd <backup folder>
mysql -u<User> -p<Password> <database> < backup.sql
```


[[Mysqldump參數大全](https://segmentfault.com/a/1190000000621104)]