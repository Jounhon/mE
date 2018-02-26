---
title: "[cmd] 取得系統時間"
date: 2018-02-26 11:38:51
categories:
	- Develop
tags:
	- cmd
---

命令提示字元取得系統時間

<!-- more -->

Code :
```
for /f "skip=1" %%x in ('wmic os get localdatetime') do if not defined MyDate set MyDate=%%x
set today=%MyDate:~0,4%%MyDate:~4,2%%MyDate:~6,2%
echo %today%

set currentTime=%MyDate:~8,2%:%MyDate:~10,2%:%MyDate:~12,2%
echo %currentTime%
```

Output :
```
20180226
11:48:08
```
