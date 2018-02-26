---
title: "[Tomcat] Setting"
date: 2018-02-26 13:41:45
categories:
	- Develop
tags:
	- Tomcat
	- Server
---

Tomat Server 環境設定

<!-- more -->


## Server啟動/關閉

開啟資料夾至` ~/bin/`

1. 啟動
> 執行 ` startup.bat`

2. 關閉
> 執行 ` shutdown.bat`

***
## Server.xml設定

開啟資料夾至` ~/conf/` ， 打開 ` server.xml`
![](tomcat-server-path.png)

-- 主要修改
``` xml
<Connector port="80" protocol="HTTP/1.1"
 connectionTimeout="20000"
 redirectPort="8443"
 maxPostSize="104857600"
 maxSavePostSize="104857600" />
```
> 104857600 = 100MB 
> -1 = 沒有限制

其他參數請參考
- [Apache Tomcat Configuration Reference - The HTTP Connector](https://tomcat.apache.org/tomcat-5.5-doc/config/http.html)
- [配置Tomcat Server](http://netkiller.sourceforge.net/www/tomcat/server.html)
- [Tomcat server.xml中Connector配置參數詳解](http://www.cnblogs.com/nihaorz/p/6702612.html)

***
## Manager啟用與設定

開啟資料夾至` ~/conf/` ， 打開 ` tomcat-users.xml`
![](tomcat-users-path.png)
將
``` xml
<user username="tomcat" password="<must-be-changed>" roles="tomcat"/>
<user username="both" password="<must-be-changed>" roles="tomcat,role1"/>
<user username="role1" password="<must-be-changed>" roles="role1"/>
```
改成
``` xml
<user username="tomcat" password="tomcat" roles="tomcat"/>
<user username="both" password="both" roles="tomcat,role1"/>
<user username="role1" password="role1" roles="role1"/>
```
在最後加上
``` xml
<role rolename="manager-gui"/>
<user username="tomcat" password="s3cret" roles="manager-gui"/>
```
![](tomcat-users-xml.png)

> 保留內建的資料夾 ( ` ~/webapps/manager` & ` ~/webapps/host-manager` )
![](tomcat-manager.png)

重新啟動 tomcat , 在網址輸入 ` localhost/manager` , 可進入監測頁面
![](tomcat-manager-web.png)

***
## JVM監測

打開 ` C://Program Files/Java/jdkx.x.x_xxx/bin/jvisualvm.exe`
![](jvm-exe.png)

可以監測 JVM的使用情形
![](jvm.png)

***
## Tomcat環境變數設定
開啟資料夾至` ~/bin/`

### 使用 ` tomcat?w.exe`

> ` tomcat?w.exe` , ` ?` 表示版本

``` bash
cd ~/bin
service install
```
![](tomcat-service.png)

點擊` comcat9w.exe` 執行
![](tomcatxw-exe.png)


### 修改 ` catalina.bat`

在檔案最前面加入設定參數
``` bash
set "JAVA_OPTS=%JAVA_OPTS% -server -Xms3000M -Xmx3000M -Xss512k -XX:+AggressiveOpts -XX:+UseBiasedLocking -XX:PermSize=128M -XX:MaxPermSize=256M -XX:NewRatio=4 -XX:SurvivorRatio=4"
```
> 參數依硬體有所差異，需依實際狀況調整數字

- [通向架构师的道路（第四天）之Tomcat性能调优](http://blog.csdn.net/lifetragedy/article/details/7708724)
- [tomcat catalina.sh JAVA_OPTS参数说明与配置](http://blog.csdn.net/cuker919/article/details/8233821)

