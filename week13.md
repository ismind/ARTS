## A: [25. Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)
```
Given a linked list, reverse the nodes of a linked list k at a time and return its modified list.  

k is a positive integer and is less than or equal to the length of the linked list.   
If the number of nodes is not a multiple of k then left-out nodes in the end should remain as it is.
```
### Example:
```
Given this linked list: 1->2->3->4->5  

For k = 2, you should return: 2->1->4->3->5  

For k = 3, you should return: 3->2->1->4->5  
```
### Note:
+ Only constant extra memory is allowed.
+ You may not alter the values in the list's nodes, only nodes itself may be changed.
---
```
  1. 在纸上画着，思考怎么做，突然想到这不就是，把链表分成（size / k） + 1 段么?size为链表长度；
  1是最后一段小于等于k的，可以为null。
  2. 那么对每一小段reverse，再拼接起来不就可以了么？这不就是一个动态规划么，哎呀，我可真是个小天才。
  3. 我去，每一段的尾部如何衔接到下一段的头，怎么存这些变量，我哭了。在下认输，喵喵别人怎么做的。
```
```java
public ListNode reverseKGroup(ListNode head, int k) {
        int n = 0;
        for (ListNode i = head; i != null; n++, i = i.next);
        
        ListNode dmy = new ListNode(0);
        dmy.next = head;
        for(ListNode prev = dmy, tail = head; n >= k; n -= k) {
            for (int i = 1; i < k; i++) {
                ListNode next = tail.next.next;
                tail.next.next = prev.next;
                prev.next = tail.next;
                tail.next = next;
            }
            
            prev = tail;
            tail = tail.next;
        }
        return dmy.next;
    }
```
