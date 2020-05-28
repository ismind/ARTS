## A: 698. Partition to K Equal Sum Subsets
（put the solution link: https://leetcode.com/problems/partition-to-k-equal-sum-subsets/discuss/108730/JavaC%2B%2BStraightforward-dfs-solution）

```javascript
public boolean canPartitionKSubsets(int[] nums, int k) {
        int sum = 0;
        for(int num:nums)sum += num;
        if(k <= 0 || sum%k != 0)return false;
        int[] visited = new int[nums.length];
        return canPartition(nums, visited, 0, k, 0, 0, sum/k);
    }
    
    public boolean canPartition(int[] nums, int[] visited, int start_index, int k, int cur_sum, int cur_num, int target){
        if(k==1)return true;
        if(cur_sum == target && cur_num>0)return canPartition(nums, visited, 0, k-1, 0, 0, target);
        for(int i = start_index; i<nums.length; i++){
            if(visited[i] == 0){
                visited[i] = 1;
                if(canPartition(nums, visited, i+1, k, cur_sum + nums[i], cur_num++, target))return true;
                visited[i] = 0;
            }
        }
        return false;
    }
```
   Thinking:
   1. Oh, it cost me about one hour to understand, and I just grasp a part of this solution's meaning.
   2. I write down the process how the recursion go in the paper.Althoght I get a little, but I further make sense of this problem, which is a relief to me.

## R : The first article is about 4 minutes to finish
(link: https://blog.bitsrc.io/code-principles-every-programmer-should-follow-e01bfe976daf). 

1. Bit.dev is possibly helpful to frontend progrommer, howerver, I have more knowledge about backend.
2. The picture under the YAGNI title is interseting. I translate it into Chinese:
   - 我们为app做了一个最快的引擎  
   - 那个鞍座是做什么用的？ 
   - 这就是那个app，我们花了不少预算在这个引擎上。
   （本来是要做app的，却专注于引擎上）
   The picture tell us it is not necessary to code for functionality that you may need in the future.
   Simply put — live in the present, not in the future.(简而言之，活在当下)
3. Clean code is better than clever code.(不要花里胡哨)Because you need to work with team not yourself, you should write understandable
code rather than a riddle for others. On other's standpoint, if they write a clever code rather clean code, how would you feel?
4. Finally, I repeat the famous words: "Any fool can write code that a computer can understand. Good programmers write code that humans can understand."
  
