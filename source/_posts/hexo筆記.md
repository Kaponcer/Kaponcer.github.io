---
title: hexo筆記
date: 2019-02-10 19:21:34
categories:
 - hexo
tags:
 - hexo
 - next theme
 - github
 - markdown

---

- ### URL標籤 #
```markdown
{% link text url [external] [title] %}
<!-- Example -->
{% link Google https://www.google.com.tw %}
```

 
<!-- more -->
- ### 程式碼展示特殊顯示 #
```markdown
 第一種
 {% codeblock [lang:language] [title] [url] [link text] %}
    展示的程式碼
 {% endcodeblock %}
 <!-- Example -->
 {% codeblock lang:objc %}
 [rectangle setX: 10 y: 10 width: 20 height: 20];
 {% endcodeblock %}
```
第二種是使用 來進行包覆 

  highlight.js 教程 第三方程式碼高亮展示
  https://vxhly.github.io/2017/10/hexo-next-advanced-settings/

 關於 lang的內容簡寫可在以下網址查詢
 {% link 程式語言名稱與簡寫 https://highlightjs.readthedocs.io/en/latest/css-classes-reference.html#language-names-and-aliases language-names-and-aliases %}

- ### Hexo 插入 數學公式 #
 #### 安裝 ####
```shell
$ npm install hexo-math --save
```

 #### 設定 ####
 + 在網站設定文件_config.yml下添加以下內容

```md
math:
  engine: 'mathjax' # or 'katex'
  mathjax:
# src: custom_mathjax_source
  config:
# MathJax config
```

 + 在next主題設定文件_config.yml下搜尋以下內容

```md
# MathJax Support
mathjax:
enable: true
per_page: false
cdn: //cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML
```
 
 
 




