---
title: HTML 筆記
date: 2020-06-13 13:11:19
comments: true
categories: html
tags:
 - html
 - 前端
---

# HTML為定義網頁的結構的標記語言. #

```html
<html> <!--- 表示網頁內容 --->
    <head>　<!--- 給瀏覽器的其他資訊 --->
        <title> Sample html</title> <!--- 標題 --->
    </head>
    <body><!--- 網頁的主體 --->
    </body>
</html>
```
# 區塊
```html
<div>這是一個區塊</div>
```

# 段落
```html
<p> 這是一個段落</p>
```
# 圖片
```html
<img src="pic/123.jpg" alt="替代文字">
<!--- 或是 --->
<figure>
    <img src="pic/123.jpg" alt="替代文字">
    <figcaption>"圖片的簡單描述"</figcaption>
</figure>
```

# 超連結(錨點) #
```html
<a href="www.google.com">Google</a>
```

# 清單
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
# 表格
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
