---
title: linux tarball安裝
categories: linux
comments: true
date: 2019-02-17 19:18:32
tags:
 - linux
 - tarball
---

#### TarBall安裝步驟 ####

TarBall安裝是Unix-like 的一種安裝方式，主要由三個步驟所構成：
1. 下載原始碼並解壓縮
```shell
download source
tar zxf source -C doc
```
2. 設定安裝參數
```shell
./configure …...
```
3. 編譯及安裝
```shell
make
make install
```

<!-- more -->

#### 至於為什麼要使用TarBall來安裝軟體呢? ####
在於Unix-like系統的軟體通常都會先釋出原始碼來讓使用者測試，等一段時間後一些線上更新的伺服器才會把它們編譯並包裝起來來供人更新。
但是使用者有時候想自己使用最新的版本的軟體該怎樣辦。這時候就要使用TarBall的方式來安裝。
由於TarBall安裝是使用原始碼來安裝，所以有時候會有相依性問題以及編譯器問題要自行解決，若沒必要不建議使用TarBall安裝的方式。以免自行移除的麻煩性。

這裡要講要如何好管理TarBall安裝的軟體，這是在使用Unix-like系統之前就要決定的事項，否則胡亂安裝，會導致更新及移除的麻煩。

#### 軟體安裝目錄及規劃 ####
1. /usr
	通常是放置發行版所包裝的軟體位置
	在這裡通常放置各使用者會用到的共同軟體，大多的情況不會使用tarball安裝．
2. /usr/local
    過去放置第三方軟體的地方，內含多個子目錄如：bin、lib...等等
	現在定義為放置自行撰寫的程式或系統．
3. /opt
	放置第三方軟體的地方，
4. /home/usr
	使用者的家目錄，為個人使用軟體的放置位置
	
規劃

| 目錄 | 目的 |
| :------ | :------ |
| /usr/local |放置自行開發上線的軟體|
| /usr/local/lib |放置自行開發的軟體所需要的相依性套件(函式庫)|
| /opt/[softwareName] | 放置tarball安裝的軟體|
|/opt/lib|放置tarball安裝的函式庫|
|/opt/src|放置tarball安裝軟體的原始碼|
|/home/usr|放置測試自行開發的軟體|
|/home/usr/src|放置測試自行開發的軟體原始碼|
|/home/usr/lib|放置測試自行開發的相依性套件(函式庫)|

#### 安裝步驟 ####
	解壓縮=>./configure ...參數  =>make=> make install
	./configure --help 可查詢可設定的安裝參數(如安裝目錄及相依性套件位址)

#### 安裝技巧 ####

下載Apache及相依性套件
Apache官網下載：http://httpd.apache.org/download.cgi
Apache的相依性套件如下:
APR + APR-Util：http://apr.apache.org/download.cgi
PCRE：http://sourceforge.net/projects/pcre/files/pcre/
安裝相依性套件
APR及APR-Util安裝
解壓縮APR及APR-Util
```shell
sudo tar zxvf apr-1.4.6.tar.gz -C /opt/src
sudo tar zxvf apr-util-1.4.1.tar.gz -C /opt/src
```
建立套件安裝目錄
```shell
sudo mkdir -p /opt/lib/apr/apr-1.4.6
sudo mkdir -p /opt/lib/apr-util/apr-util-1.4.1
```
建立軟鏈接(預設)至安裝目錄[未來更新新版本時，只要修改鏈接就可以減少相依性的修改問題]
```shell
sudo ln -s /opt/lib/apr/apr-1.4.6 /opt/lib/apr/default
sudo ln -s /opt/lib/apr-util/apr-util-1.4.1 /opt/lib/apr-util/default
```

安裝APR及APR-Util
```shell
cd /opt/src/apr-1.4.6
sudo ./configure --prefix=/opt/lib/apr/default
sudo make
sudo make install

cd /opt/sources/apr-util-1.4.1
sudo ./configure --prefix=/opt/lib/apr-util/default --with-apr=/opt/lib/apr/default
sudo make
sudo make install
```

安裝PCRE
首先請確定系统安裝了Perl，Perl在此不再赘述，如有需要請去官網查看安裝细則：http://www.cpan.org/src/README.html
解壓縮PCRE
```shell
sudo tar zxvf pcre-8.30.tar.gz -C /opt/src
```
建立PCRE安裝目錄及軟鏈接
```shell
sudo mkdir -p /opt/lib/pcre/pcre-8.30
sudo ln -s /opt/lib/pcre/pcre-8.30 /opt/lib/pcre/default
```
安裝PCRE
```shell
cd /opt/src/pcre-8.30
sudo ./configure --prefix=/opt/lib/pcre/default
sudo make
sudo make install
```
安裝Apache 2.4
解壓縮Apache 2.4
```shell
sudo tar zxvf httpd-2.4.2.tar.gz -C /opt/src
```
建立Apache安裝目錄及軟鏈接
```shell
sudo mkdir -p /opt/software/httpd/httpd-2.4.2
sudo ln -s /opt/software/httpd/httpd-2.4.2 /opt/software/httpd/default
```
安裝Apache
```shell
cd /opt/src/httpd-2.4.2

# 此處請根據自己要搭建的環境進行配置
sudo ./configure --prefix=/opt/software/httpd/default --enable-so --enable-rewrite=shared --with-mpm=prefork --with-apr=/opt/lib/apr/default --with-apr-util=/opt/lib/apr-util/default --with-pcre=/opt/lib/pcre/default

sudo make
sudo make install
```
啟動Apache
通過apachectl啟動Apache
```shell
sudo /opt/software/httpd/default/bin/apachectl start
```
檢查是否有Apache程序
```shell
ps aux | grep httpd
```
如果有Apache的程序，則證明啟動成功，瀏覽器位址欄输入 http://localhost 試試吧～
起動成功之後，可以將apachectl複製到/etc/init.d下，作为service啟動。
建立預設的httpd 軟鏈接
```shell
sudo ln -s /opt/software/httpd/default/bin/apachectl /etc/init.d/httpd
```
作為服務啟動
```shell
sudo service httpd start
```

開機時啟動Apache
編輯啟動程序
```shell
sudo vi /etc/init.d/rc.local
```
在最後一行加上 service httpd start

 
