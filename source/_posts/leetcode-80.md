---
title: leetcode-80
date: 22020-06-23 21:47:45
categories: 
 - leetcode
 - 1.array
 - medium
tags:
 - leetcode
 - array
 - medium
 - 80. Remove Duplicates from Sorted Array II
---

{% blockquote 題目 https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/ remove-duplicates-from-sorted-array-ii %}
{% endblockquote %}


問題:
給一組排序過的陣列nums，將去除重複超過兩次的值，最後再回傳不重複或出現兩次的值(重複的要保留兩個)．

<!-- more --> 

case:
{3,3,3,2,2,1,1,1,1,1} = >{3,3,2,2,1,1} return 6
{1,2,3,3,3,5}  => {1,2,3,3,5} return 5

1. 必須在同一個陣列下操作(<a href="https://en.wikipedia.org/wiki/In-place_algorithm">In-place algorithm</a>)
2. 題目沒說，升冪 降冪都可用
3. 

- 解1.　升冪 降冪都可用
  1. 設定如果陣列小於3，回傳陣列長度
  2. 設定一個index值j，這個值用儲存要放置的位址，預設為1．
  3. 設定一個計算重複次數的值count預設為1
  4. 依序尋訪nums[i]，每當找到一個與前值不同的則將nums[j]替換成新值，然後j+1，這時候count=1重新計算數量．
  5. 如果遇到重複的則看是否出現兩次以內，如果還在兩次以內就將nums[j]替換成新值且j+1；注意：不論是否兩次以內都要count+1;
  6. 最後回傳j值

```java
public int removeDuplicates(int[] nums) {
    if (nums.length < 3)
        return nums.length;
    int j = 1; // next change val
    int count = 1; // duplicates count
    for (int i = 0; i < nums.length - 1; i++) {
        if (nums[i] != nums[i + 1]) {
            nums[j++] = nums[i + 1];
            count = 1;
        } else if (count++ < 2) {
            nums[j++] = nums[i + 1];
        }
    }
    return j;

}
```

目前問題:在不考慮排序問題下，在執行之前nums內容的值，會與nums之後的內容不同．