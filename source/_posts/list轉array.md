---
title: list轉array
categories:
 - Java
 - ClassCastException

comments: true
date: 2019-03-21 16:09:10
tags:
 - java
 - ClassCastException
 - list
 - array
---
問題：
```java
List<String> list = new ArrayList<String>();
String[] array = (String[]) list.toArray();
// 編譯時，可通過；但實際上在Runtime時，會拋出ClassCastException．
```

比較好的方式
```java
List<String> list = new ArrayList<String>();
String[] array = list.toArray(new String[list.size()]);
```