//================================
##A: Leetcode-687 (https://leetcode.com/problems/longest-univalue-path/)
   1,The first time I choose this problem, I want to change another problem, because I do neither know how to solve, nor understand what 
the description means.
   After thinking, I got it!(就是说随便两个点，只要连成一条线就符合要求)Any two points which can connect into a line is right.
   Put codes here:
   /''javascript
   
   class Solution {
    int ans;
    public int longestUnivaluePath(TreeNode root) {
        ans = 0;
        arrowLength(root);
        return ans;
    }
    public int arrowLength(TreeNode node) {
        if (node == null) return 0;
        int left = arrowLength(node.left);
        int right = arrowLength(node.right);
        int arrowLeft = 0, arrowRight = 0;
        if (node.left != null && node.left.val == node.val) {
            arrowLeft += left + 1;
        }
        if (node.right != null && node.right.val == node.val) {
            arrowRight += right + 1;
        }
        ans = Math.max(ans, arrowLeft + arrowRight);
        return Math.max(arrowLeft, arrowRight);
    }
}
''/
作者：LeetCode
链接：https://leetcode-cn.com/problems/longest-univalue-path/solution/zui-chang-tong-zhi-lu-jing-by-leetcode/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
   2, Memorize and write from memory
   Learning from training camp (Geektime app), it's helpful for you to memorize solution and write down, even you can't solve 
by youself.
//================================
R: (第一次尝试用英文写评论)
   First, put the link here: https://medium.com/palantir/code-review-best-practices-19e02780015f.
Reviews:
   This article is about Code Review(CR),and explains why, what and when to review.
   I think CR essential for improving legibility,maintainability and security and so on. Althought it cost too much time in the early, 
but can save a lot of time on code's maintenance.
   This article tell us steps to review in detail,which is helpful to review.
   In the end, it's my first try to comment using English.Consequently, it's slightly weird for you to read my comments.
   Good luck.
//=================================
T: 
   Share a Git command: git mv files Files
   It can change file's name quickly on Git.
//=================================
S: 
   https://mp.weixin.qq.com/s/faUbBETPMvRtoPTGeM6aqQ
