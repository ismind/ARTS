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

## R: [4 Things That are most confusing for Java Developer](https://medium.com/the-code-monster/4-things-that-java-developer-thinks-are-most-confusing-complicated-87c2598f33f0). 
1. 这是medium上的一篇文章，写了关于下面几个主题：匿名类、多线程、synchronized、序列化与反序列化
2. 个人认为这篇文章写的很棒，对于了解这四个主题，以及相关英文，都是很大帮助
3. 其中有句话
>The main target of using the multithreading is to maximising the usage of CPU.
4. 在序列化，我测试了一下，transient和static效果一样，不将变量值写入文件中，去掉transient和static，才会写入
```javascript
private transient int nonSerializeValueSalary
```

## T : 
1. 最近写了点前台代码，position为sticky这个定位，这里是为了footer上的一个banner，让其位于页面底部，但是滚动到最底部，banner要在footer上面。
2. 另外就是学习了Tomcat 整体架构和处理请求流程解析视频，大致流程是：socket获取操作系统的数据，然后endpoint获取socket的数据，然后解析数据，经过tomcat里的容器处理，  
Engine-》Host-》Context-》Wrapper，先经过这几个容器，每个容器都有一个阀门，处理不同的事情，然后FilterChain-》Servlet，处理servlet的业务逻辑。  
当时想过为什么要分这么多容器，我想原因是要处理不同的事情。  
因为每个容器都对应这不同的功能。

## S : 
 [在 Java 虚拟机上班是一种怎样的体验？](https://mp.weixin.qq.com/s/ks_Lk68rMBHieEu-lGuPZg)
1. 我觉得这篇文章还是很幽默的，读起来很有意思，可以简单理解JVM虚拟机的内置线程。
