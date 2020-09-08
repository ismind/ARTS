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
