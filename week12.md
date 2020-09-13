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

## [142. 环形链表 II](https://leetcode-cn.com/problems/linked-list-cycle-ii/) 
1. 主要就是遍历，第一次回到环形起点，那么map中必然包含，返回即可
```
public ListNode detectCycle(ListNode head) {
        if (head == null) return null;
        ListNode next = head;
        Map<ListNode, Integer> map = new HashMap();
        while (next != null) {
           if (map.containsKey(next)) return next;
           map.put(next, next.val);
           next = next.next;
        }
        return null;
    }
```
### 2.Floyd 算法
1. 也是定义快慢指针，第二步直接搬出结论，定义一个指针从第一次相遇的节点开始，然后定义第二个指针从head开始，  
两个指针相遇就是环的起点，这是结论。
2. 原因在https://leetcode-cn.com/problems/linked-list-cycle-ii/solution/huan-xing-lian-biao-ii-by-leetcode/  
```
作为补充： 阶段2中的公式：

2(F + a) = F + a + b + a
如果写成以下会更严谨一点

2(F + a) = F + N(a + b) + a
 2F + 2a = F + 2a + b + (N - 1)(a + b)
       F = b + (N - 1)(a + b)
F是到达入口点长度
N为ptr2跑第几圈会与ptr1相遇
```
```
public ListNode detectCycle(ListNode head) {
        ListNode meet = getMeetNode(head);
        
        if (meet == null) return null;
        
        ListNode p1 = head;
        while (p1 != meet) {
            p1 = p1.next;
            meet = meet.next;
        }
        return p1;
    }
    
    public ListNode getMeetNode(ListNode head) {
        if (head == null || head.next == null) return null;
        ListNode slow = head, fast = head;
        
        while (fast.next != null && fast.next.next != null) {
            slow  = slow.next;
            fast = fast.next.next;
            if (slow == fast) return slow;
        }
        return null;
    }
```
