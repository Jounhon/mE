---
title: "[JAVA] Get Server IP"
date: 2018-02-26 10:23:51
categories:
	- Develop
tags:
	- Java
---

用JAVA 取得 server IP
<!-- more-->

Code :
``` java
import java.net.InetAddress;
import java.net.UnknownHostException;

try{
	InetAddress ipAddr = InetAddress.getLocalHost();
	String hostIP = ipAddr.getHostAddress();
	System.out.println("Server IP: " + hostIP);
}catch(UnknownHostException e){
	e.printStackTrace();
}
```

Output :

```
Server IP: 192.168.56.1
```