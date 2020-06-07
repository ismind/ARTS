这周做的不是很好，下周避免一下。这周的ARTS水了。
如果让自己给自己打分，那么给个60分，满分100。几个是因为虽然差了点，但是坚持，然后知道下次要改。
另外，自己可能走了一个极端，非要要求自己用英文来写，其实当初是要求阅读英文。

## A: 1. 两数之和
（1）暴力法
```javascript
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[j] == target - nums[i]) {
                    return new int[] { i, j };
                }
            }
        }
        throw new IllegalArgumentException("No two sum solution");
    }
```
  大家应该最先想到的就是暴力法，显然暴力法需要两层，是否可以优化呢？
  （2）一遍哈希
```javascript
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }
        throw new IllegalArgumentException("No two sum solution");
    }
```
  这种解法当然更好。
  
## R: (没有读完，挺遗憾的)
  https://levelup.gitconnected.com/how-to-use-generics-in-java-aeca75d03a6c
  这篇文章大致是将Java泛型的。

## T: 
  1. 自己遇到的一个就是notepad++的多行选择，不得不说，利用好这些工具还是能很好提高自己的效率的，
  ALt+鼠标移动
  2. 就是oracle的数字转换成字符串，如果这个数字是0.43，也就是以0.开头，那么转换的字符串会变成以.开头，
  如何转换，那就是TO_CHAR(待格式化数据, 'FM99999990.00')

## S: 
  https://mp.weixin.qq.com/s/8LXrIMOb9LUVxrNR2riDpQ
