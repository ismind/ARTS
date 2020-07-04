
## A: [10. 正则表达式匹配](https://leetcode-cn.com/problems/regular-expression-matching/). 
给你一个字符串 s 和一个字符规律 p，请你来实现一个支持 '.' 和 '*' 的正则表达式匹配。  
>'.' 匹配任意单个字符  
>'*' 匹配零个或多个前面的那一个元素  
所谓匹配，是要涵盖 整个 字符串 s的，而不是部分字符串。  
##### 说明:
+ s 可能为空，且只包含从 a-z 的小写字母。  
+ p 可能为空，且只包含从 a-z 的小写字母，以及字符 . 和 *。  
##### 示例 1:
```javascript
输入:
s = "aa"
p = "a"
输出: false
解释: "a" 无法匹配 "aa" 整个字符串。
```
##### 示例 22:
```javascript
输入:
s = "aa"
p = "a*"
输出: true
解释: 因为 '*' 代表可以匹配零个或多个前面的那一个元素, 在这里前面的元素就是 'a'。因此，字符串 "aa" 可被视为 'a' 重复了一次。
```
1. 这道题，犯的第一个错误就是没看清题目要求，*是匹配0个字符漏了，吃亏了。
2. 花了将近1个小时，不搞了，我知道是动态规划，但是写不出来，果然是困难的。
3. 我应该直接看题解，然后背下来的。
```javascript
public boolean isMatch(String s, String p) {
        int m = s.length();
        int n = p.length();

        boolean[][] f = new boolean[m + 1][n + 1];
        f[0][0] = true;
        for (int i = 0; i <= m; ++i) {
            for (int j = 1; j <= n; ++j) {
                if (p.charAt(j - 1) == '*') {
                    f[i][j] = f[i][j - 2];
                    if (matches(s, p, i, j - 1)) {
                        f[i][j] = f[i][j] || f[i - 1][j];
                    }
                }
                else {
                    if (matches(s, p, i, j)) {
                        f[i][j] = f[i - 1][j - 1];
                    }
                }
            }
        }
        return f[m][n];
    }

    public boolean matches(String s, String p, int i, int j) {
        if (i == 0) {
            return false;
        }
        if (p.charAt(j - 1) == '.') {
            return true;
        }
        return s.charAt(i - 1) == p.charAt(j - 1);
    }

作者：LeetCode-Solution
链接：https://leetcode-cn.com/problems/regular-expression-matching/solution/zheng-ze-biao-da-shi-pi-pei-by-leetcode-solution/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

## R: [Understanding Java Streams](https://medium.com/swlh/understanding-java-streams-e0f2df12441f). 
1. 这篇文章真的值得再看一遍，第一遍看了大概
2. 我觉得放在分享里也不为过。

## S : [我的大学四年收获及工作感悟](https://mp.weixin.qq.com/s/qAovoRFNkMeMNS-4pZ0fLg). 
+ 这篇文章是张一鸣老师写的，我觉得写的不错，有老师个人的见解与思想。  
> 以下是我个人的思考与收获  
---
```javascript
盲目的模仿别人，别人的成功并不适合自己，而是应该思考，学习别人的长处，别人能成功，除了这些长处之外，还有其他的因素。  
我所学到的：  
1. 需要耐心；2，多阅读；3，结交伙伴  
工作上的：
1. 有责任心，对于自己的事情，尽力做好
2. 价值观，或者说心胸。他认为青霉素能消炎，先想到救人，而不是赚钱！
3. 不自满，不懈怠，设定高远的目标。
4. 不傲娇，不骄傲，不眼高手低。  

老师关于熬夜，我觉得不适合自己，我还是早睡早起好点，没有必要的事情就不熬夜。

另外，老师借助修电脑成功撩到了小姐姐，而且将其转正了！可以，很优秀。  
我个人体会是：我很尊重张一鸣老师，因为他做到了IT的顶尖，说明必定有过人之处，有值得我学习之处正如他尊敬Elon Mask。  
我觉得短短一篇文章，只是老师的一个侧面反应，反应出他的一部分思想，但是还是有可取之处。  
在此送上我的敬意和感谢。
```
---
