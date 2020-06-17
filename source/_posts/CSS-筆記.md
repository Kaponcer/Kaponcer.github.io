---
title: CSS 筆記
date: 2020-06-17 09:46:25
comments: true
categories: html
tags:
 - html
 - 前端
---
- <a href="#margin">margin、padding、border</a>
- <a href="#text">文字</a>
- <a href="#descriptive">語意化</a>

1. <a id="margin"> margin、padding、border </a>

    ```html
        <style>
            .test {
                margin: 0px; /** 與其他元素的距離**/           width: 320px; /** 元素的寬度 **/
                border: 2px solid rgb(167, 66, 133); /** 邊框粗細、種類、顏色 **/
                padding: 20px; /** 邊框與元素內容的距離 **/
                background-color: rgb(128, 230, 81); /** 邊框內的背景顏色 **/
                color: #363fbd; /** 元素內容顏色 **/
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

2. <a id="text">文字</a>

    ```html
        <style>
            .test {
                font-size: 20px;
                /** 文字大小  20像素**/
                line-height: 2;
                /** 行高 2行行高 **/
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
    效果如下

    <div style= "font-size: 20px;line-height: 2;">
        <a href="#" style=""> this is a link </a>
        <h1 style="text-align: left;text-decoration: overline;">H1 標題</h1>
        <h2 style="text-align: center;text-decoration: line-through;">H2 標題</h2>
        <h3 style="text-align: right;text-decoration: underline;">H3 標題</h3>
        <p style="text-transform: uppercase;">This is some text.</p>
        <p style="text-transform: lowercase;">This is some text.</p>
        <p style="text-transform: capitalize;">This is some text.</p>

        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vel harum alias itaque incidunt tenetur nesciunt
        ducimus ratione eligendi. Totam at omnis nobis dicta nemo neque eaque esse illum laborum possimus.
    </div>

3. <a id="descriptive">語意化</a>
