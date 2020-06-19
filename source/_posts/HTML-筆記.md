---
title: HTML 筆記
date: 2020-06-13 13:11:19
comments: true
categories: html
tags:
 - html
 - 前端
---
<div style=" border: 1px solid;">

 # <p id="catlog" style=" text-align: center;"> 目錄 </a> #
- <a href="#goal"> HTML 的目標 </a>
- <a href="#area">  區塊 </a>
- <a href="#p"> 段落 </a>
- <a href="#pic"> 圖片 </a>
- <a href="#href"> 超連結（錨點） </a>
- <a href="#list"> 清單 </a>
- <a href="#table"> 表格 </a>
- <a href="#descriptive">語意化</a>

</div>



<!-- more -->



# <a id="goal" href="#catlog"> HTML 的目標 </a> #

 HTML 為定義網頁的結構的標記語言。

```html
<html> <!--- 表示網頁內容 --->
    <head>　<!--- 給瀏覽器的其他資訊 --->
        <title> Sample html</title> <!--- 標題 --->
    </head>
    <body><!--- 網頁的主體 --->
    </body>
</html>
```

# <a id="area" href="#catlog">  區塊 </a>

```html
<div>這是一個區塊</div>
```
<a href="/2020/06/17/CSS-筆記/">div tag CSS float</a>

# <a id="p" href="#catlog"> 段落 </a>

```html
<p> 這是一個段落</p>
```

# <a id="pic" href="#catlog"> 圖片 </a>

```html
<img src="pic/123.jpg" alt="替代文字">
<!--- 或是 --->
<figure>
    <img src="pic/123.jpg" alt="替代文字">
    <figcaption>"圖片的簡單描述"</figcaption>
</figure>
```

# <a id="href" href="#catlog"> 超連結（錨點） </a> #

```html
<a href="www.google.com">Google</a>
```

# <a id="list" href="#catlog"> 清單 </a>

```html
<ul><!--- 無序清單 --->
    <li></li> <!--- list item --->
    <li></li>
    <li></li>
    <li></li>
</ul>
<ol><!--- 有序清單 --->
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ol>
```

# <a id="table" href="#catlog"> 表格 </a>

```html
<table><!--- 表格 --->
    <tr><!--- 標題列 ---->
        <th></th><!--- 標題欄 ---->
        <th></th>
        <th></th>
    </tr>

    <tr><!--- 列 --->
        <td></td>
        <td></td><!---欄 --->
        <td></td>
    </tr>
    <tr>
        <td rowspan="2" ></td><!---rowspan 垂直跨"列" --->
        <td colspan="2"></td> <!---colspan 水平跨"欄" --->
    </tr>
    <tr>
        <td></td><td></td><td></td>
    </tr>
</table>
```

# <a id="descriptive" href="#catlog">語意化</a>

    ```html
    ```
