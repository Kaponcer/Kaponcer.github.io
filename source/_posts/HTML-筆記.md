---
title: HTML 筆記
date: 2020-06-13 13:11:19
comments: true
categories: html
tags:
 - html
 - 前端
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

- <a href="#goal"> HTML 的目標 </a>
- <a href="#basicElement"> 基本元素 </a>
    - <a href="#area">  區塊 </a>
    - <a href="#p"> 段落 </a>
    - <a href="#pic"> 圖片 </a>
    - <a href="#href"> 超連結（錨點） </a>
    - <a href="#list"> 清單 </a>
    - <a href="#table"> 表格 </a>
- <a href="#elementType">區塊元素、行內元素</a>

</div>



<!-- more -->



- # <a id="goal" href="#catlog"> HTML 的目標 </a> #

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
- # <a id="basicElement" href="#catlog"> 基本元素 </a> #
    - ## <a id="area" href="#catlog">  區塊 </a> ##
    ```html
    <div>這是一個區塊</div>
    ```
    {% blockquote  CSS案例 <a href="/2020/06/17/CSS-筆記/#floatdiv">div tag CSS float</a> %}
    {% endblockquote %}
    {% blockquote  CSS案例 <a href="/2020/06/17/CSS-筆記/#boxsizing">box-sizing</a> %}
    {% endblockquote %}
    - ## <a id="p" href="#catlog"> 段落 </a>

    ```html
    <p> 這是一個段落</p>
    ```

    - ## <a id="pic" href="#catlog"> 圖片 </a>

    ```html
    <img src="pic/123.jpg" alt="替代文字">
    <!--- 或是 --->
    <figure>
        <img src="pic/123.jpg" alt="替代文字">
        <figcaption>"圖片的簡單描述"</figcaption>
    </figure>
    ```

    - ## <a id="href" href="#catlog"> 超連結（錨點） </a> #

    ```html
    <a href="www.google.com">Google</a>
    ```

    - ## <a id="list" href="#catlog"> 清單 </a>

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

    - ## <a id="table" href="#catlog"> 表格 </a>

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

- # <a id="elementType" href="#catlog">區塊元素、行內元素</a>
    <p class="description"><strong>區塊元素(block)</strong><em>是一種占用整行大小的元素</em>，雖然可以設定寬、高，但是下個元素還是會列在下一行，並不會排列再一起；</p>
    <p class="description"><strong>行內元素(inline)</strong>基本上是沒有寬(width)跟高(height)，當兩個行內元素排列時，並<em>不會占用整行，而是依自己的元素內容而定</em>．
    </p>

| 元素 | 行內元素、區塊元素 |
| :------: | :------: |
| div | 區塊元素 |
| p | 區塊元素 |
| img | 行內元素(可以有寬高)算是(inline-block) |
| a | 行內元素 |
| ul ol li | 區塊元素 | 
| table tr |  區塊元素（會排除除了tr th td以外的元素) |
| td | 行內元素(一般的情況下沒辦法跟其他行內元素再一起，因為父元素會排除其他元素) |

{% blockquote CSS案例： <a href="/2020/06/17/CSS-筆記/#inline-block">inline block inline-block</a> %}
{% endblockquote %}



