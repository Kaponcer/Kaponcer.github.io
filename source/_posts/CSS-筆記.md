---
title: CSS 筆記
date: 2020-06-17 09:46:25
comments: true
categories:
    - html
    - css
tags:
 - css
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

<div style=" border: 1px solid;">

# <p id="catlog" style=" text-align: center;"> 目錄 </a> #

- <a href="#margin">margin、padding、border</a>
- <a href="#text">文字</a>
- <a href="#floatdiv">float</a>
- <a href="#inline-block">inline block inline-block</a>
- <a href="#boxsizing">box-sizing</a>
- <a href="#CSSReset">CSS Reset & CSS Normalize</a>
- <a href="#flex">flex</a>
- <a href="#position">position</a>
- <a href="#hover">:hover</a>
</div>

<!-- more -->

- # <a id="margin" href="#catlog"> margin、padding、border </a> #

    ```html
        <style>
            .test {
                margin: 0px;
                 /** 與其他元素的距離 border之外的範圍**/
                width: 320px;
                 /** 元素的寬度 **/
                border: 2px solid rgb(167, 66, 133);
                 /** 邊框粗細、種類、顏色 **/
                padding: 20px; /** 邊框與元素內容的距離 **/
                background-color: rgb(128, 230, 81);
                 /** 邊框內的背景顏色 **/
                color: #363fbd;
                 /** 元素內容顏色 **/
            }
            .aaa {
                margin: 10px;
                width: 320px;
                border: 2px solid rgb(167, 66, 133);
                padding: 20px;
                background-color: rgb(128, 230, 81);
                color: #363fbd;
            }
        </style>
    ```

    效果如下
<div style=" margin: 0px;width: 320px;border: 2px solid rgb(167, 66, 133);padding: 20px;background-color: rgb(128, 230, 81);color: #363fbd;">
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vel harum alias itaque incidunt tenetur nesciunt
    ducimus ratione eligendi. Totam at omnis nobis dicta nemo neque eaque esse illum laborum possimus.
</div>
<div style=" margin: 10px;width: 320px;border: 2px solid rgb(167, 66, 133);padding: 20px;background-color: rgb(128, 230, 81);color: #363fbd;">
    <p>this is a aaa.</p>
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vel harum alias itaque incidunt tenetur nesciunt
    ducimus ratione eligendi. Totam at omnis nobis dicta nemo neque eaque esse illum laborum possimus.
</div>

- # <a id="text" href="#catlog">文字</a> #

    ```css
        <style>
            .test {
                font-size: 20px;
                /** 文字大小  20像素**/
                line-height: 5;
                /** 行高 3行行高 **/
                white-space: nowrap;
                /* 超過寬度不換行 */
                 text-indent: 2em;
                /* 縮排兩字元，如果要凸排，改成負數就可以達成效果 */
                /*  px像素(代表螢幕的pixel)
                    em字元(代表每個字的大小，會依照"父元素"font-size而變)
                    rem字元 (代表每個字的大小，會依照"Root元素"font-size而變)*/

            }
            .shadow{
            text-shadow: 5px   5px      2px    red;
            /* 文字陰影 向右偏移 向下偏移 淺景深  陰影顏色 */
            }

            .test a {
                text-decoration: none;
                /* 標線 底線消除*/
                color: red;
                /* 文字顏色 */
            }

            .test h1 {
                text-align: left;
                /* 文字對齊*/
                text-decoration: overline;
                /* 上標線 */
            }

            .test h2 {
                text-align: center;
                /* 文字對齊*/
                text-decoration: line-through;
                /* 刪除線*/
            }

            .test h3 {
                text-align: right;
                /* 文字對齊*/
                text-decoration: underline;
                /* 下標線*/
            }

            .uppercase {
                text-transform: uppercase; /* 全大寫*/
            }

            .lowercase {
                text-transform: lowercase; /*全小寫*/
            }

            .capitalize {
                text-transform: capitalize; /*首字都大寫*/
            }
        </style>
    ```

    效果如下（有另加一個 border 比較好觀看範圍）

<div style= "border: 1px solid; font-size: 20px;line-height: 3;white-space: nowrap; text-indent: 2em;">
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vel harum alias itaque incidunt tenetur nesciunt
    ducimus ratione eligendi. Totam at omnis nobis dicta nemo neque eaque esse illum laborum possimus.<br/>
    <a href="#" style="text-decoration: none;color: red;"> this is a link </a>
    <p style="text-shadow: 5px   5px      2px    red;">SHADOW</p>
    <h1 style="text-align: left;text-decoration: overline;">H1 標題</h1>
    <h2 style="text-align: center;text-decoration: line-through;">H2 標題</h2>
    <h3 style="text-align: right;text-decoration: underline;">H3 標題</h3>
    <p style="text-transform: uppercase;">This is some text.</p>
    <p style="text-transform: lowercase;">This is some text.</p>
    <p style="text-transform: capitalize;">This is some text.</p>
</div>

- # <a id="floatdiv" href="#catlog">float</a> #

## 案例樣式表 ##

```css
*{ /* 這是為了清空預設格式 */
    margin: 0;
    padding: 0;
}
.container{
    width:960px;
    background-color: rgb(0, 163, 192);
    margin:auto;/* 置中對齊 */
}
.col {
    width:200px;
    height:200px;
    margin:10px;
    background-color: #fff;
    float: right;　/* 靠右對齊 */
}
.container-height-fix{
    clear:both;
}
.col2 {
    width:200px;
    height:200px;
    margin:10px;
    background-color: rgb(129, 35, 35);
    float: left;　/*靠右對齊*/
}
```

## 案例１ ## 
<p id="floatCase1" class="description"> 在這裡會發現，container的背景顏色會消失，是因為他的子元素的CSS樣式有float樣式，擁有float樣式的元素會跳脫原本的父元素，而這裡的.container會因為沒有子元素，且沒有設定height樣式，導致它不會出現在上面． </p>

```html
<div class="container">
    <div class="col"></div>
    <div class="col"></div>
    <div class="col"></div>
</div>
```

<strong>解決方案</strong>
```html
<div class="container">
    <div class="col"></div>
    <div class="col"></div>
    <div class="col"></div>
    <!-- 這是用來將上面的float樣式消除的方法，請參考上面的樣式表-->
    <div class="container-height-fix"></div>
</div>
```

## 案例２ ##
<p class="description"> 在這裡會發現.col2的元素被擠到下面去了．原因是.col2上面還有一個.container-height-fix的元素．如果要在同一行的話只要把col2換到.container-height-fix上面就行了．但是如果只是要讓.container包覆住.只要在下面再多加一行.container-height-fix的元素就好了．在這裡可以了解到<strong>clear:both會有所謂的換行效果</strong>．</p>
```html
<div class="container">
    <div class="col"></div>
    <div class="col"></div>
    <div class="col"></div>
    <!-- 這是用來將上面的float樣式消除的方法，請參考上面的樣式表-->
    <div class="container-height-fix"></div>
    <div class="col2"></div>
</div>
```

<strong>解決方案</strong>
```html
<!-- 換行效果 -->
<div class="container">
    <div class="col"></div>
    <div class="col"></div>
    <div class="col"></div>
    <!-- 這是用來將上面的float樣式消除的方法，請參考上面的樣式表-->
    <div class="container-height-fix"></div>
    <div class="col2"></div>
    <div class="container-height-fix"></div>
</div>
```

```html
<!-- 同行效果 -->
<div class="container">
    <div class="col"></div>
    <div class="col"></div>
    <div class="col"></div>
    <div class="col2"></div>
    <!-- 這是用來將上面的float樣式消除的方法，請參考上面的樣式表-->
    <div class="container-height-fix"></div>
</div>
```
- # <a id="inline-block" href="#catlog">inline block inline-block</a> #

## 案例樣式表 ##

```css
* {
    /* 這是為了清空預設格式 */
    margin: 0;
    padding: 0;
}

.div {
    margin: 20px;
    border: 1px solid ;
    background-color: #515faf;
}
ol{
    margin: 5px;
    border: 1px solid red;
    text-align: center;
}
li{
    border: 5px solid orange;
    width: 100px;
    margin: 10px ;
    padding: 5px;
    background-color: white;
}
.inline {
    display: inline;
}

.block {
    display: block;
}

.inlineblock {
    display: inline-block;
}
```

## 案例１ ##
<p class="description">我們知道div、ol、li都是區塊元素，這時候我們將li標籤display樣式分別顯示inline、block、inline-block會有怎麼樣的情況，注意我們只有li的display標籤不同，其餘的都相同</p>

```html
<div>
    <p>這是li標籤display樣式為inline</p>
    <ol>
        <li class="inline">item</li>
        <li class="inline">item</li>
        <li class="inline">item</li>
        <li class="inline">item</li>
    </ol>
</div>
<div>
    <p>這是li標籤display樣式為block</p>
    <ol>
        <li class="block">item</li>
        <li class="block">item</li>
        <li class="block">item</li>
        <li class="block">item</li>
    </ol>
</div>
div>
    <p>這是li標籤display樣式為inline-block</p>
    <ol>
        <li class="inlineblock">item</li>
        <li class="inlineblock">item</li>
        <li class="inlineblock">item</li>
        <li class="inlineblock">item</li>
    </ol>
</div>
<div>
    <p>這是li標籤display樣式為none，簡單講就是不給看也不會分配空間．</p>
    <ol>
        <li class="none">item</li>
        <li class="none">item</li>
        <li class="none">item</li>
        <li class="none">item</li>
    </ol>
</div>
```

- # <a id="boxsizing" href="#catlog">box-sizing</a> #

## 案例樣式表 ##
```css
.origin,.boxsizing{
    float: right;
    margin: 2px ;
}
div div {
    margin: 5px auto;
    border:5px solid red;
    width: 200px;
    height: 100px;
}
.origin {
    background-color: #351;
}

.boxsizing {
    background-color: #555555;
    /* width為border以內(border也包含)來做計算 */
}
.origin div {
    /* box-sizing: content-box; 預設選項，如果沒有特別設定 */
}

.boxsizing div{
    box-sizing: border-box;
}
.clearfix{
    clear: both;
}
.width200{
    width: 200px;
}
.border20{
    border:20px solid red;
}
p{
    font-size: 20px;
    text-align: center;
    color: silver;
}
```
## 案例１ ##
<p class="description">在之前我們了解了margin、border、padding、content這之間的關係，用來計算合適的width．這裡透過一個box-sizing的樣式來讓我們，更方便去計算每個html元素的width．</p>


```html
<div class="origin">
    <p>Origin</p>
    <div class="width200">Width=200px border=5px</div>
    <div class="width200 border20">Width=200px border=20px</div>
</div>

<div class="boxsizing">
    <p>boxsizing</p>
    <div class="width200">Width=200px border=5px</div>
    <div class="width200 border20">Width=200px border=20px</div>
</div>
<div class="clearfix"></div>
```

- # <a id="CSSReset" href="#catlog">CSS Reset & CSS Normalize</a> #
    <p class="description">
    <strong>CSS Reset</strong>：CSS樣式重置，因為各個瀏覽器會原本的預設樣式會有不同的CSS樣式，<strong>開發者為了完全的控制樣式</strong>，所以會一開始重置CSS樣式．</p>

    {% blockquote CSS Reset https://meyerweb.com/eric/tools/css/reset/  Eric Meyer %}

    ```css
    /* http://meyerweb.com/eric/tools/css/reset/ 
    v2.0 | 20110126
    License: none (public domain)
    */

    html, body, div, span, applet, object, iframe,
    h1, h2, h3, h4, h5, h6, p, blockquote, pre,
    a, abbr, acronym, address, big, cite, code,
    del, dfn, em, img, ins, kbd, q, s, samp,
    small, strike, strong, sub, sup, tt, var,
    b, u, i, center,
    dl, dt, dd, ol, ul, li,
    fieldset, form, label, legend,
    table, caption, tbody, tfoot, thead, tr, th, td,
    article, aside, canvas, details, embed, 
    figure, figcaption, footer, header, hgroup, 
    menu, nav, output, ruby, section, summary,
    time, mark, audio, video {
        margin: 0;
        padding: 0;
        border: 0;
        font-size: 100%;
        font: inherit;
        vertical-align: baseline;
    }
    /* HTML5 display-role reset for older browsers */
    article, aside, details, figcaption, figure, 
    footer, header, hgroup, menu, nav, section {
        display: block;
    }
    body {
        line-height: 1;
    }
    ol, ul {
        list-style: none;
    }
    blockquote, q {
        quotes: none;
    }
    blockquote:before, blockquote:after,
    q:before, q:after {
        content: '';
        content: none;
    }
    table {
        border-collapse: collapse;
        border-spacing: 0;
    }
    ```
    {% endblockquote %}
    <p class="description">
    <strong>CSS Normalize</strong>：CSS正規化，當CSS重置時，樣式都歸０，使得有些有用的css樣式，也必須重新設定，CSS Normalize 就跟著孕育而生．</p>
    {% blockquote  CSS Normalize.css的目標 http://nicolasgallagher.com/about-normalize-css/  normalize.css %}
    - <strong>保留有用的瀏覽器預設值</strong>，而非消除它．
    - 替廣泛的HTML元素提供<strong>正規化樣式</strong>．
    - <strong>修正問題(bugs)</strong>及瀏覽器間的不一致．
    - 透過部分的修改來<strong>改善可用性</strong>．
    - 使用註解以及提供細部文件來<strong>說明程式碼</strong>．
    {% endblockquote %}






- # <a id="flex" href="#catlog">flex</a> #

## 案例一 ##
```css
/* 在這裡就會開始引用CSSReset，這裡不另做匯入，
    詳情請參考CSS Reset & CSS Normalize說明 */
.container {
    width: 960px;
    background-color: #be97fd;
    margin: 10px auto;
}

.flexContainer {
    display: flex;
    flex-wrap: wrap;
}

.item {
    width: 300px;
    margin: 10px;
    box-sizing: border-box;
}

.item h2 {
    text-align: center;
    font-size: 36px;
}

.item img {
    width: 100%
}

.item p {
    margin: 10px;
}

.flexItem {}
```

```html
<div class="container flexContainer">
    <div class="flexItem item"><img src="https://fakeimg.pl/300x200/ffffaa/" alt="">
        <h2>Item1</h2>
        <P>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Doloribus magnam incidunt similique, voluptatem
            repellat fuga cumque harum laudantium possimus perspiciatis veniam necessitatibus nam, veritatis dolores
            magni ipsam earum et corrupti.</P>
    </div>
    <div class="flexItem item"><img src="https://fakeimg.pl/300x200/ffffaa/" alt="">
        <h2>Item2</h2>
        <P>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Doloribus magnam incidunt similique, voluptatem
            repellat fuga cumque harum laudantium possimus perspiciatis veniam necessitatibus nam, veritatis dolores
            magni ipsam earum et corrupti.</P>
    </div>
    <div class="flexItem item"><img src="https://fakeimg.pl/300x200/ffffaa/" alt="">
        <h2>Item3</h2>
        <P>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Doloribus magnam incidunt similique, voluptatem
            repellat fuga cumque harum laudantium possimus perspiciatis veniam necessitatibus nam, veritatis dolores
            magni ipsam earum et corrupti.</P>
    </div>
    <div class="flexItem item"><img src="https://fakeimg.pl/300x200/ffffaa/" alt="">
        <h2>Item4</h2>
        <P>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Doloribus magnam incidunt similique, voluptatem
            repellat fuga cumque harum laudantium possimus perspiciatis veniam necessitatibus nam, veritatis dolores
            magni ipsam earum et corrupti.</P>
    </div>
    <div class="flexItem item"><img src="https://fakeimg.pl/300x200/ffffaa/" alt="">
        <h2>Item5</h2>
        <P>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Doloribus magnam incidunt similique, voluptatem
            repellat fuga cumque harum laudantium possimus perspiciatis veniam necessitatibus nam, veritatis dolores
            magni ipsam earum et corrupti.</P>
    </div>
    <div class="flexItem item"><img src="https://fakeimg.pl/300x200/ffffaa/" alt="">
        <h2>Item6</h2>
        <P>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Doloribus magnam incidunt similique, voluptatem
            repellat fuga cumque harum laudantium possimus perspiciatis veniam necessitatibus nam, veritatis dolores
            magni ipsam earum et corrupti.</P>
    </div>
</div>
```

<p class="description">這裡演示一個簡單的flex案例，flex跟float不同的地方，在於float是單一元素修改，常常要特別的撰寫才能達到內容融入的感覺，例如<a href="#floatCase1"><b>float案例</b></a>：一個有包含float的父元素，如果沒有其他內容，會讓父元素不認為有其float樣式子元素的存在，為了解決一個問題，我們需要多撰寫一個子元素，並讓它包含clear的樣式來解決這個問題．</p>

{% blockquote <a href="/2020/06/26/CSS-flex-更進一步/" target="_blank">學習flex更進一步</a>  %}
{% endblockquote %}

- # <a id="position" href="#catlog">position</a> #

## 案例樣式表 ##
```css

```
## 案例１ ##
```html


```
- # <a id="hover" href="#catlog">:hover</a> #

## 案例樣式表 ##
```css

```
## 案例１ ##
```html

```
