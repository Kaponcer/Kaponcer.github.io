---
title: linux入門常用指令(Debian系列的Linux預設軟體儲藏庫)
date: 2019-02-10 13:35:00

categories:
 - linux
 - Debian
 - Ubuntu

tags:
- ubuntu
- linux
- Debian
    
---



- ### 立即重新開機 #
```shell 
$ shutdown -r now 
```
---

- ### 立即關機 #
```shell 
$ shutdown -h now 
```
---
<!-- more -->

- ### 切換目前所在的目錄位址
```shell 
$ cd [資料夾位址] 
  #Example
$ cd ../tmp   #切換到上一頁的tmp資料夾下
$ cd ./tmp2   #切換到本頁內的tmp2資料夾下
$ cd /tmp     #切換到根目錄下的tmp資料夾下
$ cd ~        #切換到目前的家目錄
```
---
- ### 建立一個空白的檔案(某方面來說還蠻實用的)
```shell 
$ touch [路徑/檔名] 
```
---
- ### 用vi編輯器來開啟檔案
```shell 
$ vi [路徑/檔名]
```
---
- ### 移動檔案或資料夾在指定的地方(可用於修改檔名及資料夾名稱)
```shell 
$ mv [來源路徑/檔案]  [目地路徑/檔案]
#Example 
#將目前所在的資料夾下的abc.txt檔修改成def.txt檔
$ mv ./abc.txt ./def.txt
```
---
- ### 刪除檔案(無法刪除資料夾
```shell 
$ rm [路徑/檔案]
```
---
- ### 遞迴刪除某資料夾 (某方面很重要)
```shell 
$ rm -r [路徑/資料夾]
```
---
- ### 新增資料夾
```shell 
$ mkdir [路徑/資料夾名]
```
---
- ### 刪除資料夾
```shell 
$ rmdir [路徑/資料夾]
#如果資料夾下有資料則無法刪除。
#如果要刪除整個資料夾則使用rm -r 
```
---
- ### 解壓縮 .tar.gz 檔案到 目的資料夾
```shell 
$ tar zxvf [路徑/檔名] -C [目的路徑/資料夾]
```
---
- ### 使用debian系列的linux的軟體儲藏庫來安裝軟體
```shell 
$ apt-get install [軟體關鍵字]
```
---
- ### 更新軟體儲藏庫資料
```shell 
$ apt-get update
```
---
- ### 更新已安裝的軟體
```shell 
$ apt-get upgrade
```
---
- ### 使用debian系列的linux的軟體儲藏庫來移除軟體
```shell 
$ apt-get remove [軟體關鍵字]
```
---
- ### 清除無用的安裝資料
```shell 
$ apt-get autoclean 
```
---
- ### 移除無用的相依性套件
```shell 
$ apt-get autoremove
```
---
- ### 暫時使用有限制權限的root身份執行[指定的指令]
 通常用於apt-get  rm 

```shell 
$ sudo [指令]
#Example
$ sudo apt-get install git-core
# 暫時使用有限制權限的root身份安裝git-core 套件及相關套件
```
---
- ### 切換到root身分 
剛開始學盡量少用，可能會導致不可復原的問題，包含操作失敗導致系統出錯、產生出系統漏洞．
```shell 
$ sudo su
```
