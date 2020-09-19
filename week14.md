## A: [88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)  
#### Example:
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.  
### Note:
- The number of elements initialized in nums1 and nums2 are m and n respectively.
- You may assume that nums1 has enough space (size that is equal to m + n) to hold additional elements from nums2.  
### Example:
```
Input:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

Output: [1,2,2,3,5,6]
```
### Constraints:
- -10^9 <= nums1[i], nums2[i] <= 10^9
- nums1.length == m + n
- nums2.length == n
1。 这道题的思路不比merge链表，因为是数组，那么可以将nums2添加到nums1，然后对nums1排序即可
```java
public void merge(int[] nums1, int m, int[] nums2, int n) {
        for (int i = m, j = 0; i < m + n; i++, j++) {
            nums1[i] = nums2[j];
        }
        Arrays.sort(nums1);
    }
```
