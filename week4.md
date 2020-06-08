
## A: 240. Search a 2D Matrix II
（https://leetcode.com/problems/search-a-2d-matrix-ii/）
  1. 这道题估计都会想到暴力法，即两层循环搞定。那么能不能减少时间复杂度呢？优化一下
  2. 但是浏览国外的高票回答（https://leetcode.com/problems/search-a-2d-matrix-ii/discuss/66140/My-concise-O(m%2Bn)-Java-solution）  
  你会疑惑，为什么从右上角开始遍历。为什么不能从左上、左下、右下开始呢？
  3. 评论区有一张图，并说这是一棵树，你就明白了，从右上角就是二叉搜索树，特征就是所有左子树小于根，所有右子树大于根。  
  (https://assets.leetcode.com/static_assets/discuss/uploads/files/1488858512318-monosnap-2017-03-06-22-48-17.jpg)  
  其实这里左下和右上角都是一样的，都是树。这就是原因。
  ```javascrit
  public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix == null || matrix.length < 1 || matrix[0].length < 1) 
            return false;
        
        int rows = matrix.length,
            cols = matrix[0].length;
        
        int row = 0, col = cols - 1;
        
        while (col >= 0 && row < rows) {
            if (target == matrix[row][col])
                return true;
            else if (target > matrix[row][col])
                row++;
            else
                col--;
        }
        return false;
        
    }
  ```
  #### 这段代码是自己的理解，然后写的，大致思路都是一样的，我觉得这样写适合自己。
