---
title: CSS flex 更進一步
date: 2020-06-26 17:09:49
comments: true
categories:
    - html
    - css
tags:
 - css
 - 前端
 - flex
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

- <a href="#flex-word-relation">flex詞彙關係圖</a>
- <a href="#flex-direction">flex-direction</a>
</div>

<!-- more -->


# <a id="flex-word-relation" href="#catlog">flex詞彙關係圖</a>  

{% blockquote flex 詞彙表示圖 https://developer.mozilla.org/zh-TW/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes#%E5%BD%88%E6%80%A7%E7%9B%92%E5%AD%90%E7%9A%84%E5%AD%97%E5%BD%99 "MDN Developer" %}
![flex詞彙表示圖](flex_terms.png)
{% endblockquote %}

# 案例一
{% blockquote flex 案例一 <a href="/2020/06/17/CSS-筆記/#flex" target="_blank"> CSS 筆記</a> %}
{% endblockquote %}


# <a id="flex-direction" href="#catlog">flex-direction</a>  

| 值 | 如何對齊 | 
|:-----:|:-----:|
| row | 從main start開始到 main end |
| row-reverse | 從main end開始到 main start |
| column | 從cross start開始到 cross end |
| column-reverse | 從cross end 開始到 cross start |

- ## flex-direction: row;
```css
.flexContainer {
    display: flex;
    flex-wrap: wrap;
     /* 僅增加這行*/
    flex-direction: row ; /*{ row | row-reverse | column | column-reverse }*/ 
}
```
![flex direction: row;](flex-direction-row.png)
- ## flex-direction: row-reverse;
```css
.container {
    width: 1280px;
    background-color: #be97fd;
    margin: auto;
    /* 僅增加這行*/
    flex-direction: row-reverse ; /*{ row | row-reverse | column | column-reverse }*/ 
    /* 到這裡*/
}
```

![flex direction: row-reverse;](flex-direction-row-reverse.png)
- ## flex-direction: column;
```css
.flexContainer {
    display: flex;
    flex-wrap: wrap;
    /* 僅增加這兩行*/
    height: 800px; /* 如果沒有這行會只有一行，不會換欄 */
    flex-direction: column ; /*{ row | row-reverse | column | column-reverse }*/ 
}
```
![flex direction: column;](flex-direction-column.png)
- ## flex-direction: column-reverse;
```css
.container {
    width: 1280px;
    background-color: #be97fd;
    margin: auto;
    /* 僅增加這兩行*/
    height: 800px;/* 如果沒有這行會只有一行，不會換欄 */
    flex-direction: column-reverse ; /*{ row | row-reverse | column | column-reverse }*/ 
    /* 到這裡*/
}
```
![flex direction: column-reverse;](flex-direction-column-reverse.png)
