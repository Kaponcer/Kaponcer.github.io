---
title: 使用git+maven+eclipse建立簡單Java專案
categories: git
comments: true
date: 2019-02-22 14:35:10
tags:
 - java
 - eclipse
 - maven
 - git
 - github
---
1. 先建立Github 專案儲藏庫
取得Clone URL: https://github.com/USERNAME/ProjectName.git

2. 在Eclipse建立Maven Java 專案
 new->other-maven Project-> maven-archetype-quickstart 


3. 專案右鍵->Team->share Project
   ->勾選Use or create repository in parent folder of project
   ->點擊 Create Repository

4. 設定 Git .gitignore 在Eclipse Java Maven專案中設定的內容

```properties
#Eclipse
.classpath
.project
.settings/

#Maven
log/
target/
```

5. clone Github儲藏庫複製到專案資料夾下
```shell
git clone git-url
``` 
將clone下來的資料
.git/
README.md
覆蓋到專案資料夾下

#### 從github clone專案到eclipse ####

1. window/show View/Git Repositions

2. 複製Github 專案的URL

3. Git Repositions上右鍵/past repository Path or URL/該打的打一打...

4. Pockage Explorer上右鍵/import/maven->Existing Maven Project
   ->Root Directory下設定上一個步驟存的專案位址->找到後打勾就完成了

可能的錯誤:在build時可能會產生出jre錯誤，因為maven只能用jdk所以必須設定build configure,將jre設定成jdk的jre

其他種方式如:import->git專案->convert to maven project會多產生一個pom.xml檔會不順利

----------完成----------
剩下在設定POM裡面的相依性套件以及classPath相關

註:如果步驟3直接連線github會出錯，目前還找不到答案．所以才使用步驟5的方式．
如果有人找到可以直接在Eclipse裡面操作的麻煩留言告知一下,感謝.

