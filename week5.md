## A: 剑指 Offer 05. 替换空格 
https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/  
1. 这题虽然简单，但是我觉得还是动手一下，试试。  
2. 结果自己还是没有想出什么好办法，然后调用string自带的replaceAll，可是效率不高。
3. 看到说建立一个三倍长的数组，好办法，可是自己代码写的是这样的，
```javascript
public static String replaceSpace(String s) {
        char[] arr = s.toCharArray();
        int len = arr.length;

        if (len < 1) return s;
        char[] arr2 = new char[len * 3];
        for (int i = 0; i < len; i++) {
            arr2[i * 3] = arr[i];
            if (arr[i] == ' ') {
                arr2[i * 3] = '%'; arr2[i * 3 + 1] = '2'; arr2[i * 3 + 2] = '0';
            }
        }
        System.out.println(Arrays.toString(arr2));
        s = String.valueOf(arr2);

        return s;
    }

```
1）显然，还不是很好，最后只得看题解，一目了然，原来自己被自己的想法禁锢了，看了题解还是学到了。  
```javascript
public String replaceSpace(String s) {
        int length = s.length();
        char[] array = new char[length * 3];
        int size = 0;
        for (int i = 0; i < length; i++) {
            char c = s.charAt(i);
            if (c == ' ') {
                array[size++] = '%';
                array[size++] = '2';
                array[size++] = '0';
            } else {
                array[size++] = c;
            }
        }
        String newStr = new String(array, 0, size);
        return newStr;
    }

作者：LeetCode-Solution
链接：https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/solution/mian-shi-ti-05-ti-huan-kong-ge-by-leetcode-solutio/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

```   
2）再看看高票的解答，哇，更简洁，代码写的真好！
```javascript
public String replaceSpace(String s) {
        StringBuilder res = new StringBuilder();
        for(Character c : s.toCharArray())
        {
            if(c == ' ') res.append("%20");
            else res.append(c);
        }
        return res.toString();
    }

作者：jyd
链接：https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/solution/mian-shi-ti-05-ti-huan-kong-ge-ji-jian-qing-xi-tu-/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
``` 
4. 我觉得这样简单的题目，看起来简单，可是当自己真正去做，才发现自己还是有欠缺。
