---
title: 'leetcode#461'
categories: 
 - leetcode
 - easy
 - 461. Hamming Distance
comments: true
date: 2019-03-08 18:54:07
tags:
 - leetcode
 - easy
 - Hamming Distance
 - 461
---
問題:
取兩樹之間的{% link 漢明距離 https://zh.wikipedia.org/wiki/汉明距离 %}

<!-- more -->

```java
class Solution {
    public int hammingDistance(int x, int y) {
        int count =0;
        // 使用xor計算，將不同值的位元算成1
        int temp = x^y;
        while(temp>0){
            // 取餘數出來
            count+=temp%2;
            // 使用右位移1 (基本上也可以用除2)
            temp>>=1;
        }
        return count;
    }
}
```

心得:
{% blockquote %}
這是第一次使用位元移動的運算子，還以為這輩子用不太到了．
{% endblockquote %}