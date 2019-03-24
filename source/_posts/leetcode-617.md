---
title: 'leetcode#617'
categories: 
 - leetcode
 - easy
 - 617. Merge Two Binary Trees 
comments: true
date: 2019-03-10 16:13:18
tags:
 - leetcode
 - easy
 - Merge Two Binary Trees
 - 617
---

問題：
給兩個二元樹，將兩個相同位置的元素相加合併．

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
    public TreeNode mergeTrees(TreeNode t1, TreeNode t2) {
        TreeNode merged ;
        if(t1==null)
            return  t2 ;
        if(t2==null)
            return t1;
        merged = new TreeNode(t1.val+t2.val);
        merged.left = mergeTrees(t1.left,t2.left);
        merged.right = mergeTrees(t1.right,t2.right);
        return merged;
    }
}
```


心得:
{% blockquote %}
 簡單的遞迴使用.
{% endblockquote %}