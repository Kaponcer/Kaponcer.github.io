---
title: leetcode#26
date: 2020-06-23 20:24:40
categories: 
 - leetcode
 - 1.array
 - easy
tags:
 - leetcode
 - array
 - easy
 - 26. Remove Duplicates from Sorted Array
---

{% blockquote 題目: https://leetcode.com/problems/remove-duplicates-from-sorted-array/ remove-duplicates-from-sorted-array %}
{% endblockquote %}


問題:
給一組排序過的陣列nums，將不重複的值排在前面，最後再傳送這個陣列有多少個不重複的值．

<!-- more --> 

case:
{3,3,3,2,2,1,1,1,1,1} = >{3,2,1} return 3
{1,2,3,3,3,5}  => {1,2,3,5} return 4
{1,1,2,3,9} => {1,2,3,9} return 4

條件
1. 必須在同一個陣列下操作(<a href="https://en.wikipedia.org/wiki/In-place_algorithm">In-place algorithm</a>)
2. 題目沒說，升冪 降冪都可用
3. 


- 解1.　升冪 降冪都可用
  1. 設定如果陣列都沒有值就回傳0
  2. 設定一個index值j，這個值用儲存要放置的位址，預設為1．
  3. 依序尋訪nums[i]，每當找到一個與前值不同的則將nums[j]替換成新值，然後j+1
  4. 最後回傳j值(會剛好為不重複值的個數)

```java
public int removeDuplicates(int[] nums) {
    if(nums.length<1)
        return 0;
    int j = 1; // next val
    for(int i = 0;i<nums.length-1;i++){
        if(nums[i]!=nums[i+1]){
            nums[j++] = nums[i+1];
        }
    }
    return j;
}
```

目前問題:在不考慮排序問題下，在執行之前nums內容的值，會與nums之後的內容不同．
  