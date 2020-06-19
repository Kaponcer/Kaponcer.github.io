---
title: HTML5 frame 替代方案
date: 2020-06-18 10:03:46
update: 2020-06-18 14:09:20
categories:
 - html
 - question
tags:
    - html
    - jquery
    - frame
    - iframe
    - frameset
    - javascript
---
<style>
    strong { 
        text-shadow: 0.5px 0.5px red;
    }
    .description {
        text-indent: 2em;  
    }
</style>

<div style=" border: 1px solid;">

# <p id="catlog" style=" text-align: center;"> 目錄 </a> #

- <a href="#subject"> HTML5 frameset 廢棄問題 </a>
- <a href="#iframe">  方案一 使用 iframe </a>
- <a href="#object"> 方案二 方案二 使用 Object 標籤 </a>
- <a href="#javascript"> 方案三 使用 jQuery </a>
</div>


# <a id="subject" href="#catlog">  HTML5 frameset 廢棄問題 </a> #

<p class="description"> 在新版的 HTML5 中，已經不支援 frameset 以及 frame 這兩個標籤．目前 Chrome 執行下來，會只認第一個 frame 元素的內容，第二個是不會顯示出來的．
</p>

    ```html
    <!DOCTYPE html>　<!-- HTML5 -->
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
    </head>
    <frameset rows="50% 50%">
        <frame name="top" src="1.html">
            <!-- 只會顯上上面的內容　-->
        <frame name="bottom" src="2.html">
            <!-- 我不會顯示，但是程式碼還在　-->
    </frameset>
    </html>
    ```

<!-- more -->

# <a id="iframe" href="#catlog">  方案一 使用 iframe </a> #
<p class="description"> 基本上是可以使用的 , 不過據說對<strong> SEO </strong> 不太好，而且瀏覽器的相容性也不太好．大多都不會使用這個方法來組織自己的網站內容，不過如果是 <strong> 安插廣告 </strong>是不錯的選擇
    </p> 

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
        <style>
            div {
                margin: 20px;
                border: 2px solid;
                padding: 10px;
            }
        </style>
    </head>
    <body>
        <div>
            <iframe src="1.html" width="100%" height="800" frameborder="0">

                您的瀏覽器不支援iframe，請升級
            </iframe>
        </div>
        <div>
            <iframe src="2.html" width="100%" height="800" frameborder="0">

                您的瀏覽器不支援iframe，請升級
            </iframe>
        </div>
    </body>
    </html>
    ```

# <a id="object" href="#catlog">  方案二 使用 Object 標籤</a> #

<p class="description">
    這個方法比較沒有什麼問題，但是在程式碼上面<strong>會出現一個以上的html、head、body標籤</strong>，因為它是將整個網頁放在一個object標籤之內．<strong>可能會造成SEO優化問題</strong>．
    </p>


    ```html
    <!DOCTYPE html>
    <html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
    </head>

    <body>
        <div id="main" style="border: 2px solid;">
           <object type="text/html" data="1.html" width="100%" height="600px"></object>
        </div>
        <div id="main2" style="border: 2px solid;">
           <object type="text/html" data="1.html" width="100%" height="600px"></object>
        </div>
    </body>
    </html>
    ```
    
# <a id="javascript" href="#catlog">  方案三 使用 jQuery</a> #


<p class="description">
有別於Object物件的壞處，內文基本上沒有多餘的標籤，不過對於網頁結構上不太好，因為一個網頁結構需要<strong>透過javascript來處理(渲染？)</strong>有點不太適合．
</p>

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
        <script src="https://code.jquery.com/jquery-3.5.1.js"
            integrity="sha256-QWo7LDvxbWT2tbbQ97B53yJnYU3WhH/C8ycbRAkjPDc=" crossorigin="anonymous"></script>
        <script>
            $(document).ready(function(){
                $("#main").load("1.html");
                $("#main2").load("1.html");
            });
        </script>
    </head>

    <body>
        <div id="main" style="margin:10px; border: 2px solid;"></div>
        <div id="main2" style="margin:10px; border: 2px solid red;"></div>
    </body>
    </html>
    ```
    
