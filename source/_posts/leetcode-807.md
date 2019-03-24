---
title: 'leetcode#807'
categories: 
 - leetcode
 - medium
 - 807. Max Increase to Keep City Skyline
comments: true
date: 2019-03-07 20:22:03
tags:
 - leetcode
 - 807
 - Max Increase to Keep City Skyline
 - medium
---
問題翻譯：
1. 給一個二維陣列，該陣列每個元素代表一塊地，每個元素內的值代表建築物高度．
2. Keep City Skyline，代表一種建造規則，任何建築物不得建造比原本的列跟欄（column and row）最高建築的還要高．

<!-- more -->

重點:
    1 < grid.length = grid[0].length <= 50.
    All heights grid[i][j] are in the range [0, 100].
    All buildings in grid[i][j] occupy the entire grid cell: that is, they are a 1 x 1 x grid[i][j] rectangular prism.

第一版本:

```java
class Solution {
    public int maxIncreaseKeepingSkyline(int[][] grid) {
        // 因為notes有說是長方形的所以可以這樣設定
        // row=>列 ,column=>欄
        int increated = 0 ,row = grid.length,column=grid[0].length;
        // 存放從上至下最大值
        List<Integer> columnMax = new LinkedList<Integer>();
        // 存放從左至右最大值
        List<Integer> rowMax = new LinkedList<Integer>();
        
        // 陣列內容逐一尋訪
        for(int i =0;i<row;i++){
            for(int j=0;j<column;j++){
                // step1 存放從上到下最大值
                if(columnMax.size()<=j){
                    columnMax.add(grid[i][j]);
                }else if(columnMax.get(j)<grid[i][j]){
                    columnMax.set(j,grid[i][j]);
                }
                // step2 存放從左至右最大值
                if(rowMax.size()<=i){
                    rowMax.add(grid[i][j]);
                }else if(rowMax.get(i)<grid[i][j]){
                    rowMax.set(i,grid[i][j]);
               }
            }
        }
        // step3 將建造差新增到increated
        for(int i =0;i<row;i++){
            for(int j=0;j<column;j++){
                if(columnMax.get(j).compareTo(rowMax.get(i))>0){
                    increated+=(rowMax.get(i)-grid[i][j]);
                }else{
                    increated+=(columnMax.get(j)-grid[i][j]);
                }
                    
            }
        }
         return increated;
    }
   
}
```
心得：
{% blockquote %}
本題是第一次做medium的難度，花在理解題目的時間，比解題的時間還要多．一直在思考Skyline，再說些什麼．
{% endblockquote %}