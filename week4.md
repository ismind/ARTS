
## A: 240. Search a 2D Matrix II
https://leetcode.com/problems/search-a-2d-matrix-ii/
  1. 这道题估计都会想到暴力法，即两层循环搞定。那么能不能减少时间复杂度呢？优化一下
  2. 但是浏览国外的高票回答 https://leetcode.com/problems/search-a-2d-matrix-ii/discuss/66140/My-concise-O(m%2Bn)-Java-solution  
  你会疑惑，为什么从右上角开始遍历。为什么不能从左上、左下、右下开始呢？
  3. 评论区有一张图，并说这是一棵树，你就明白了，从右上角就是二叉搜索树，特征就是所有左子树小于根，所有右子树大于根。  
  https://assets.leetcode.com/static_assets/discuss/uploads/files/1488858512318-monosnap-2017-03-06-22-48-17.jpg
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

## R: 
### https://medium.com/rtkal/distributed-cache-design-348cbe334df1
1. 这篇文章主要讲了分布式缓存，为什么使用、哪些场景用到、分布式缓存如何工作、缓存驱逐策略、常用的分布式缓存。
2. 感觉还是很好的，对于了解一些最新的英文技术词汇还是不错的。时间保持在几分钟或者10分钟左右。

### https://medium.com/better-programming/which-java-microservice-framework-should-you-choose-in-2020-4e306a478e58
1. 这篇文章是关于截至目前（2020），各种微服务框架性能之间的比较。
2. 作者自己通过自己的实际操作，比较了Spring、Micronaut、Quarkus、Helidon MicroProfile等之间的优劣。
3. 分别从1）实现简单应用的难易 2）编译应用的时长 3）启动应用的时长 4）处理请求个数
4. 最后评估各种结果（文章有讲到，就不翻译了。）
5. 个人认为，这篇文章还是很精彩的，对于学习词汇很有帮助。

## T:
   None。
   
## S:
   https://mp.weixin.qq.com/s/1LHraeRhcYoxY03VS7Riag  
   bobo老师的文章，确实是有深度和来自他的思考。还是不错的。
