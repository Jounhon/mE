---
title: Android Studio with Genymotion
date: 2018-02-26 09:56:32
categories:
	- Develop
tags:
	- Android Studio
	- Genymotion
---

Android Studtion 加入 Genymotion 模擬器
<!-- more -->

## 安裝

\> [Genymotion Download](https://www.genymotion.com/fun-zone/)<
-- 需要先有帳號才能下載

***
## 設置

### SDK Path (Genymotion)
![](genymotion-setting.png)

-- 選擇 ` Use custom Android SDK tools` > ` Browse` > ` Android SDK Path`

[ Android SDK Path通常放在 ` C:/Users/[user]/AppData/Local/Android/sdk` ]

![](genymotion-setting-2.png)

### Genymotion Plugin (Android Studio)

` File` > ` Settting`
![](android-setting.png)

-- `Plugins` > `Browser respositories...` > 搜尋 `Genymotion` > `Install`
![](android-setting-plugin.png)

-- `Restart Android Studio`
![](android-setting-plugin-2.png)

-- 重啟後會看見多一個圖示，點擊後可以選擇要開啟的模擬器
![](android-genymotion.png)

-- 成功啟動模擬器
![](android-vm.png)

***

## ARM Translation

\> [` Genymotion ARM Translation`]()<
> 安裝路徑不能有中文路徑，不然會無法順利安裝

-- 將zip檔拖入模擬器，會有粉紅色框框出現，將檔案丟進去

![](genymotion-arm.png)

![](genymotion-arm-2.png)

![](genymotion-arm-3.png)

-- 安裝後關掉模擬器，再重新啟動

-- 執行app

![](android-run-app.png)
