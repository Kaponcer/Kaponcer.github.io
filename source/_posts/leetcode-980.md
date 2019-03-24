---
title: 'leetcode#980'
categories: 
 - leetcode
 - hard
 - 980. Unique Paths III 
 
comments: true
date: 2019-03-10 16:00:54
tags:
 - leetcode
 - hard
 - Unique Paths III
 - #980
---
問題:
　　給一個二維陣列裡面包含1、2、0、-1這幾個數，1代表起點，2代表終點，0代表可走的路徑，-1代表障礙物．求出從起點到終點有多少路徑，期間所有的0都比須都曾通過，並不進行重複通過．

<!-- more -->

第一版本
```java
class Solution {
    class Step {
		// 存放已走過的路
		public List<Step> walked = new LinkedList<Step>();
		public int obstaclesCount = 0;
		public Step from = null;
		// 目前位址(row,column)
		public final int row, column;

		Step(int i, int j) {
			this.row = i;
			this.column = j;
			walked.add(this);
		}

		Step(int i, int j, List<Step> walked, Step from) {
			this(i, j);
			this.from = from;
			this.walked.addAll(walked);
		}

		public boolean canWalking(int x) {
			switch (x) {
			case 1:
				return true;
			case 2:
				return true;
			case 0:
				return true;

			}
			return false;
		}

		public int walking(int[][] grid) {
			int count = 0;
			if (grid[row][column] == -1) {
				System.out.println("-1");
				return 0;
			}
			if (grid[row][column] == 2) {
				if (this.walked.size() + obstaclesCount == grid[0].length * grid.length)
					return 1;

				return 0;
			}
			if (grid[row][column] == 0 || grid[row][column] == 1) {
				// 往上走
				if (row > 0) {
					if (canWalking(grid[row - 1][column])) {
						Step top = new Step(row - 1, column, walked, this);
						if (!walked.contains(top)) {
							top.obstaclesCount = this.obstaclesCount;
							count += top.walking(grid);
						}
					}
				}
				// 往下走
				if ((row + 1) < grid.length) {
					if (canWalking(grid[row + 1][column])) {
						Step bottom = new Step(row + 1, column, walked, this);
						if (!walked.contains(bottom)) {
							bottom.obstaclesCount = this.obstaclesCount;
							count += bottom.walking(grid);
						}
					}
				}
				// 往左走
				if (column > 0) {
					if (canWalking(grid[row][column - 1])) {

						Step left = new Step(row, column - 1, walked, this);
						if (!walked.contains(left)) {
							left.obstaclesCount = this.obstaclesCount;
							count += left.walking(grid);
						}
					}
				}
				// 往右走
				if ((column + 1) < grid[0].length) {
					if (canWalking(grid[row][column + 1])) {
						Step right = new Step(row, column + 1, walked, this);
						if (!walked.contains(right)) {
							right.obstaclesCount = this.obstaclesCount;
							count += right.walking(grid);
						}
					}
				}
			}
			return count;
		}

		@Override
		public boolean equals(Object obj) {
			if (obj instanceof Step) {
				Step step = (Step) obj;
				if (step.row == this.row && step.column == this.column)
					return true;
			}
			return false;
		}

	}

	public int uniquePathsIII(int[][] grid) {
		// 陣列中的寬跟長
		int rowMax = grid.length, columnMax = grid[0].length;
		// 障礙數
		int obstaclesCount = 0;
		// 起始點
		Step start = null;
		for (int i = 0; i < rowMax; i++) {
			for (int j = 0; j < columnMax; j++) {
				if (grid[i][j] == 1)
					start = new Step(i, j);
				if (grid[i][j] == -1)
					obstaclesCount++;
			}
		}

		if (start != null) {
			start.obstaclesCount = obstaclesCount;
			return start.walking(grid);
		}

		return 0;
	}
}

```

心得:
{% blockquote %}
第一次做hard難度，效能上跟其他人比慢很多，之後可能還會再改寫．去除掉沒什用到、以及重複的程式碼在優化第一版本．別人的解有點看不太懂，之後再研究．
{% endblockquote %}