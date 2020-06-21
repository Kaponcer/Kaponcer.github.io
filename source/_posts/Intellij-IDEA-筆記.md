---
title: Intellij IDEA 筆記
date: 2020-06-21 12:50:37
categories:
 - Java
 - IDE
comments: true
tags:
 - java
 - IDE
---

<style>
    strong { 
        text-shadow: 0.5px 0.5px red;
    }
    .description {
        text-indent: 2em;  
    }
</style>


<div style=" border: 1px solid;"><!-- 下面要空一行不然會出錯 -->
<b style="font-size:32px"> <p id="catlog" style=" text-align: center;"> 目錄 </a> </b><br/>

- <a href="#descript">說明</a>
- <a href="#hotkey">快捷鍵</a>
- <a href="#webProject">建立預設的Servlet&JSP專案(網頁)</a>
    - <a href="#webProjectCreate"> 建立 </a>
    - <a href="#webProjectDeploy"> 部屬 </a>
    - <a href="#webProjectStart"> 啟動 </a>
    - <a href="#tomcatSSL"> HTTPS (SSL) </a>
-
</div>


<!-- more -->


- # <a id="descript" href="#catlog">說明 </a> #
   <p class="description"> 下定決心，刷了一年份買付費版．</p>
- # <a id="hotkey" href="#catlog">快捷鍵 </a> #
| 快捷鍵          | 用途           | 
| :-------------- | --------------: |
| ctrl + alt + L  | 快速排版      |
|        |                         |
|        |                        |
|                 |                |

- # <a id="webProject" href="#catlog">建立預設的Servlet&JSP專案(網頁) </a> #
    - ## <a id="webProjectCreate"  href="#catlog"> 建立 </a> ##
        1. File -> New -> Project
        {% blockquote 圖1.1 建立新的web專案  %}
        ![NewWebProject](NewWebProject.png)
        {% endblockquote %}
        <br/>
        {% blockquote 圖1.2 設定專案名稱 %}
        ![NewWebProjectName.png](NewWebProjectName.png)
        {% endblockquote %}
        <br/>
    - ## <a id="webProjectDeploy"  href="#catlog"> 部屬 </a> ##
        1. Run -> Edit Configurations...
        {% blockquote 圖1.3 以tomcat為例，設定前畫面，請點選右上角的Create configuration %}
        ![tomcatConfig1](tomcatConfig1.png)
        {% endblockquote %}
        <br/>
        {% blockquote 圖1.4 Server頁面，紅框的地方請記得設定 %}
        ![tomcatConfig2](tomcatConfig2.png)
        {% endblockquote %}
        <br/>
        <p class="description"> 姑且說一下，從最上面的紅框是設定這個設定的名稱，舉例來說，在測試環境中可能會選擇tomcat Server進行部屬，但是最後部屬可能不會在本地，應該說大多得情況都不是在本地。所以根據不同情況有可能會有一堆部屬設定檔． 第二個紅框是設定tomcat程式的所在地．第三個是設定JRE環境．(有種講廢話的感覺)</p>

        {% blockquote 圖1.5 Deployment頁面，旁邊的＋點選後選擇Artifact.. %}
        ![tomcatConfig3](tomcatConfig3.png)
        {% endblockquote %}
        <br/>
        {% blockquote 圖1.6 Deployment頁面，這時候出現預設的部屬內容，可以再看Server頁面那邊看也有些變化（請先不要改）．看了之後記一下那裡變了，之後就點選下面的OK %}
        ![tomcatConfig4](tomcatConfig4.png)
        {% endblockquote %}
        <br/>
    - ## <a id="webProjectStart"  href="#catlog"> 啟動 </a> ##
        1. Run -> Run 'Sample'
        {% blockquote 圖1.7 如果沒意外的話應該瀏覽器會跳出標題為 $TITLE$ 內文 $END$的畫面 %}
        ![start Project](start.png)
        {% endblockquote %}
        <br/>
        在這裡可能會出現一個問題，有些瀏覽器強制HTTPS連線，而現在的情況卻只能HTTP連線而已.
    - ## <a id="tomcatSSL"  href="#catlog"> HTTPS (SSL) </a> ##
        1. 準備憑證，使用JDK內附的keytool 公用程式．
        ```bash
        # keytool -genkey -alias 憑證的名稱 -keyalg RSA -storepass keystore的密碼 #
        keytool -genkey -alias tomcat -keyalg RSA -storepass StorePassword -keystore localhost-rsa.jks
        ```
        {% blockquote 圖1.8 實際產生key畫面 %}
        ![genSSLkey](genSSLkey.png)
        {% endblockquote %}<br/>
        <p class="description"><strong>在這裡要注意我是把localhost-rsa.jks放在tomcat/conf/資料夾下</strong></p>
        2. 編輯server.xml檔案，開啟HTTPS服務
        {% blockquote 圖1.9 編輯tomcat/conf/server.xml %}
        ![configServer.xml](configServerxml.png)
        {% endblockquote %}<br/>
        3. 設定Port
        {% blockquote 圖1.10 IDE 設定部分 %}
        ![configPortInIDE.xml](configPortInIDE.png)
        {% endblockquote %}<br/>
        <p>這裡設定兩個地方，先將原本的http改成https，再來我這邊Chrome不認localhost來源的憑證，還好有127.0.0.1可以用，如果是firefox就可以用Localhost，不過要加入例外清單；第二個設定的地方是將8443port加入https上</p>
        {% blockquote 圖1.11 成果 %}
        ![httpsSccess](httpsSccess.png)
        {% endblockquote %}<br/>
        {% blockquote 生成自簽憑證-參考資料 https://tomcat.apache.org/tomcat-9.0-doc/ssl-howto.html self-signed certificate %}
        {% endblockquote %}<br/>
        {% blockquote Tomcat SSL設定-參考資料 https://tomcat.apache.org/tomcat-9.0-doc/config/http.html#SSL_Support SSL Configuration %}
        {% endblockquote %}<br/>
        