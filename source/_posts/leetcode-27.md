---
title: leetcode#27
date: 2020-06-22 20:30:16
categories: 
 - leetcode
 - array
 - easy
 - 461. Remove Element
tags:
 - leetcode
 - array
 - easy
 - 461. Remove Element
---

問題:
給一組陣列nums跟一個int val，將與val相同的都在最後面的位置，最後再傳送這個陣列有多少個值與val不同．
- 解1.
  每找到一個與val不同的值(nums[j])跟之前的第一個與val相同的值(nums[i])做交換
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int count = 0;
        int i = 0;// first equal val
        int j = 0;// first not equal val
        while(j<nums.length){
            if(nums[j]!=val) {
                if(i!=j){
                    int temp = nums[j];
                    nums[j] = nums[i];
                    nums[i] = temp;
                }
                i++;
                count++;
            }
            j++;
        }
        return count;
    }
}
```
演算法解釋:
每找到一個與val值相同(nums[i])，與最後一個跟val不同(nums[j])的值做交換．直到i >= j;
- 解2.
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int j = nums.length;
        for(int i = 0;i < j;i++){
            if (nums[i] == val) {/* first equal val */
                while (--j > i && nums[j] == val) {// search last value of not equal "val"
                }
                int tmp = nums[j]; // change value;
                nums[j] = nums[i];
                nums[i] = tmp;
            }
        }
        return j;
    }
}
```