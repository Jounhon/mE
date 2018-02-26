---
title: "[cmd] 取得批次所在路徑"
date: 2018-02-26 11:49:54
categories:
	- Develop
tags:
	- cmd
---

命令提示字元取得批次所在路徑

<!-- more -->

Code :
```
SET mypath=%~dp0
cd "%mypath:~0,-1%"
```
