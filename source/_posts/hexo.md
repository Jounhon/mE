---
title: 快速架設 Hexo 網誌框架
date: 2018-02-22 15:45:48
categories:
	- Develop
tags:
	- Hexo 
	- Markdown
---

使用Hexo快速建立markdown網誌。

<!-- more -->

## 安裝與建置

### 安裝
使用套件管理工具
- [Node.js]()
- [yarn [optional]]()
安裝完成後，使用需要的指令，即可安裝Hexo。
npm:
` npm install -g hexo-cli`
如果有安裝yarn，執行下面指令:
` yarn global add hexo-cli`

### 建置
安裝Hexo完成後，執行下列指令
npm:
```
hexo init <folder> && cd <folder>
npm install
```

yarn:
```
hexo init <folder> && cd <folder>
yarn
```
***

## 配置
可以在 ` _config.yml` 中修改大部分的配置


### Site

| 參數  | 說明  |
| :---- | :---- |
| title | 網站標題 |
| subtitle | 網站副標題 |
| author | 作者 |
| language | 網站語言(zh-tw) |
| timezone | 網站時區 |

- 其他參數說明請參考 [Hexo文件](https://hexo.io/zh-cn/docs/index.html)
***

## 指令

### 建立新Post

``` bash
hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### 產生靜態文件 Generate
```
hexo generate
```
可簡寫為
```
hexo g
```

參數

| 選項 | 說明 |
| :--- | :--- |
| -w , --watch | 監看文件變動 |
| -d , --deploy | 文件產生後立即部署到網站 |

e.g. : ` hexo g -w`

More info: [Generating](https://hexo.io/docs/generating.html)

### 啟動服務 Server

預設網址為: ` http://localhost:4000/`
```
hexo server
```
可簡寫為
```
hexo s
```

參數

| 選項 | 說明 |
| :--- | :--- |
| -p , --port | 設定port |
| -s , --static | 使用靜態文件 |
| -l , --log | 啟用日記記錄 |

e.g. : ` hexo s -p3000` 設定port=3000

More info: [Server](https://hexo.io/docs/server.html)

### 部署網站Deploy

``` bash
hexo deploy
```
可簡寫為
```
hexo d
```
More info: [Deployment](https://hexo.io/docs/deployment.html)

***

## 主題

### NexT

```
cd <folder>
git clone https://github.com/iissnan/hexo-theme-next themes/next
```

修改 ` ~/_config.yml`  
將 ` Theme:` 改成 ` Theme: next` 

修改 ` ~/thmems/next/_config.yml`

#### Site Information Settings 
```
Footer:
	since: yyyy 
```
` yyyy` = 開始年

#### Menu Settings
```
menu:
	key: /link/ || icon
menu_icons:
	enable: true
```
` link` = target
` icon` = name of FontAwesome icon

#### Scheme Settings
共4個主題可以選擇：` Muse` ,` Mist` ,` Pisces` ,` Gemini`
選擇要的主題將前面的` #` 拿掉即可。

#### Sidebar Settings
```
social:
	key: link || icon

#頭像
avatar: image
```

- NexT主題配置請參考 [NexT主題配置](http://theme-next.iissnan.com/theme-settings.html)

***

## 搜尋

npm:
```
cd <folder>
npm install hexo-generator-search --save
```
yarn:
```
cd <folder>
yarn add hexo-generator-search
```

修改 ` ~/thmems/next/_config.yml`
```
local_search:
  enable: true
```

***

## 選單

修改 ` ~/thmems/next/_config.yml`
```
menu:
  home: / || home
  about: /about/ || user
  categories: /categories/ || th
  tags: /tags/ || tags
  archives: /archives/ || archive
```

### 分類 Categories
```
hexo new page categories
```
open ` ~/source/categories/index.md`
```
---
  title: 分類
  date: 2018-02-22 15:09:48
  type: "categories"
---
```

### 標籤 Tags
```
hexo new page tags
```
open ` ~/source/tags/index.md`
```
---
  title: 標籤
  date: 2018-02-22 15:00:41
  type: "tags"
---
```
***