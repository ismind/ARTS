## A:  139. 单词拆分
https://leetcode-cn.com/problems/word-break/  
给定一个非空字符串 s 和一个包含非空单词列表的字典 wordDict，判定 s 是否可以被空格拆分为一个或多个在字典中出现的单词。

#### 说明：

+ 拆分时可以重复使用字典中的单词。
+ 你可以假设字典中没有重复的单词。
示例 1：  

>输入: s = "leetcode", wordDict = ["leet", "code"]  
>输出: true  
>解释: 返回 true 因为 "leetcode" 可以被拆分成 "leet code"。  

示例 2：  
>输入: s = "applepenapple", wordDict = ["apple", "pen"]  
>输出: true  
>解释: 返回 true 因为 "applepenapple" 可以被拆分成 "apple pen apple"。  
> 注意你可以重复使用字典中的单词。

示例 3：  
>输入: s = "catsandog", wordDict = ["cats", "dog", "sand", "and", "cat"]   
>输出: false
---
自己的思考：
1. 首先我想，既然是，那就用“减法”好了，用s减去list里的，不就可以了么，但是实现起来并不好做。
2. 然后我又想将s转换成数组，即char[a[i] - 'a']，然后list里出现的字母，就char[a[i] - 'a']--，但是忘记了s里可以有重复，而list里无重复
3. 时间花了二十多分钟，看题解。
```javascript
public boolean wordBreak(String s, List<String> wordDict) {
        Set<String> wordDictSet = new HashSet(wordDict);
        boolean[] dp = new boolean[s.length() + 1];
        dp[0] = true;
        for (int i = 1; i <= s.length(); i++) {
            for (int j = 0; j < i; j++) {
                if (dp[j] && wordDictSet.contains(s.substring(j, i))) {
                    //记录下符合要求的分割点,下次直接在if里使用就好了
                    //真的很巧妙
                    dp[i] = true;
                    break;
                }
            }
        }
        return dp[s.length()];
    }

作者：LeetCode-Solution
链接：https://leetcode-cn.com/problems/word-break/solution/dan-ci-chai-fen-by-leetcode-solution/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```
+ 不好理解，要花一些时间。
