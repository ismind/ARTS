## A: [24. Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/) 
Given a linked list, swap every two adjacent nodes and return its head.   
You may not modify the values in the list's nodes, only nodes itself may be changed.    
#### Example:
```javascript
Given 1->2->3->4, you should return the list as 2->1->4->3.
```
1. recursive(niubi)
```javascript
public class Solution {
    public ListNode swapPairs(ListNode head) {
        if ((head == null)||(head.next == null))
            return head;
        ListNode n = head.next;
        head.next = swapPairs(head.next.next);
        n.next = head;
        return n;
    }
}
```
2. iterative
```javascript
public class Solution {
    public ListNode swapPairs(ListNode head) {
        if (head == null || head.next == null) return head;
        ListNode cur = head;
        ListNode newHead = head.next;
        while (cur != null && cur.next != null) {
            ListNode tmp = cur;
            cur = cur.next;
            tmp.next = cur.next;
            cur.next = tmp;
            cur = tmp.next;
            if (cur != null && cur.next != null) tmp.next = cur.next;
        }
        return newHead;
    }
}
```

## [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) 
1. 这道题，再做一遍，思路很明显，就是用两个指针，一个快、一个慢，如果有环，那么快的一定会追上慢的。
2. 可是自己写了多次，不明白问题再哪里。
```javascript
public boolean hasCycle(ListNode head) {
        if (head == null) return false;
        ListNode slow = head, fast = head;
        while (slow.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) return true;
        }
        return false;
    }
```
一直显示while判断那里为空异常java.lang.NullPointerException  
3. 原来存在fast.next为空，那么fast.next.next自然就报错了，所以更换判断条件为
```javascript
while (fast.next != null && fast.next.next != null) {
```
it works!
