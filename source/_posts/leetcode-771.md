---
title: 'leetcode#771'
categories: 
 - leetcode
 - easy
 - 771. Jewels and Stones
comments: true
date: 2019-03-07 10:44:41
tags:
 - leetcode
 - 771
 - Jewels and Stones
 - easy
---

問題：
字串 J是寶石的集合，每個字元代表一種寶石，Ｓ字串則是一堆石頭集合，每個字元代表一顆石頭，需要找Ｓ中，有多少Ｊ裡面的寶石．

註：大小寫為不相同的，例如：大寫Ａ跟小寫a代表不同的寶石．

<!-- more -->

```Java
// 第一版本
class Solution {
    public int numJewelsInStones(String J, String S) {
        // 分解問題[(J1與S做比較)+(J2+J3+..Jn與S做比較)]
        if(J.length()>1){
            return numJewelsInStones(J.substring(0,1),S)+numJewelsInStones(J.substring(1),S);
        }
        // 這時J的數量只有１,最後再與S逐一比對
        int i =0;
        for(char a:S.toCharArray()){
            if(a==J.charAt(0))
                i++;
        }
        return i;
    }
}
```
目前找到第一個版本有一個錯誤
test case: J="aAa" S="aAAbbbb" Output= 4 Expected=3

```java
// 第二版本
class Solution {
    public int numJewelsInStones(String J, String S) {
        // 將J放入Set中
        Set<Character> Jewels = new HashSet<Character>();
        for (char j :J.toCharArray()){
            Jewels.add(j);
        }
        // 將S裡面的石頭,逐一比對樣式寶石(Jewels)
        int  count=0;
        for(char s: S.toCharArray()){
            if(Jewels.contains(new Character(s)))
                count++;
        }
        return count;
    }
}
```


