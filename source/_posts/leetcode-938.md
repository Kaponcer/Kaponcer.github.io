---
title: 'leetcode#938'
categories: 
 - leetcode
 - medium
 - 938. Range Sum of BST #938
comments: true
date: 2019-03-07 21:16:56
tags:
 - leetcode
 - medium
 - #938
 - Range Sum of BST
---

問題:
給一個二元搜尋樹,還有兩個值,將二元搜尋樹內介於這兩個值的元素相加．

<!-- more -->

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public int rangeSumBST(TreeNode root, int L, int R) {
        if(root!=null){
            if(root.val<L){
                return rangeSumBST(root.right,L,R);
            }else if(root.val>R){
                return rangeSumBST(root.left,L,R);
            }else{
                return rangeSumBST(root.left,L,R)+root.val+rangeSumBST(root.right,L,R);
            }
        }
         return 0;
    }          
}
```

心得：
{% blockquote %}
這題很簡單，只要了解它定義的二元搜尋樹，就可以使用遞迴解決．
{% endblockquote %}