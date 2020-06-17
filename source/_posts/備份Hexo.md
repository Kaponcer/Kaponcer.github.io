---
title: 備份Hexo
categories: 
 - hexo
comments: true
date: 2020-06-12 11:54:38
tags:
 - hexo
 - next theme
 - github
 - markdown
---
<div style=" border: 1px solid;">

 # <p id="catlog" style=" text-align: center;"> 目錄 </a> #
- <a href="#backup">備份</a>
- <a href="#recover">還原</a>
</div>


<!-- more -->


# <a id="backup" href="#catlog">備份</a> #
1. 確認.gitignore 內如是否包含如下
```.gitignore
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```
2. Git指例
```bash
git init
#建立git儲存庫(原本就存在gitignore是因為hexo本身就會產生)
git checkout -b hexo
#建立一個名為hexo的分支，用來存放備份資料
git add .
#將目前目錄下的內容加入git追蹤
git commit -m "第一次備份"
#寫入儲存庫
git remote add  origin https://github.com/username/username.github.io.git
#加入遠端儲存庫位址(基本上只要第一次)(註:不要跟著我打網址，要看您的遠端位址)
git push --setupstream=origin/hexo
#推送本次commit到遠端資儲存庫
```

# <a id="recover" href="#catlog">還原</a> #

```bash
  hexo init
  mkdir gitback
  cd ../..
  git checkout hexo
  #切換到hexo分支(之前備份到這裡的分支)
  #根據不同的情況看下面的作法
  ```
1. 備份的版本跟新地點一樣
   
   覆蓋就可以了

2. 備份的版本比新地點還舊
   
   將舊的_config.yml逐一對照新的_config.yml，逐一修改在新的＿config.yml上．並確認您的模組及theme是否還會正常．例如：hexo-math在Hexo4.1之後就會出現出錯.(需要找其他替代模組)