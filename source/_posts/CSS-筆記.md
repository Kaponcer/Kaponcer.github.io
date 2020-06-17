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
<div style=" border: 1px solid;">

 # <p id="catlog" style=" text-align: center;"> 目錄 </a> #
- <a href="#margin">margin、padding、border</a>
- <a href="#text">文字</a>
- <a href="#descriptive">語意化</a>
</div>



<!-- more -->



#  1.  <a id="margin" href="#catlog"> margin、padding、border </a> #

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

#  2. <a id="text" href="#catlog">文字</a> #

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

    效果如下(有另加一個border 比較好觀看範圍)

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

3. 