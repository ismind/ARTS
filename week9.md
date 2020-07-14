## A: [剑指 Offer 18. 删除链表的节点](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)  
## [203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)
Remove all elements from a linked list of integers that have value val.  
#### Example:
```javascript
Input:  1->2->6->3->4->5->6, val = 6
Output: 1->2->3->4->5
```
1. 其实这两道题目类似，解法可以理解为相同。外文的votes较高的，看了一下，然后自己做了两遍。
```javascript
public ListNode removeElements(ListNode head, int val) {
        ListNode fakeHead = new ListNode(-1);
        fakeHead.next = head;
        if (head == null) return null;
        ListNode prev = head, curr = fakeHead;
        while (prev != null) {
            if (prev.val == val) 
                curr.next = prev.next;
            else
                curr = curr.next;
            prev = prev.next;
        }
        return fakeHead.next;
        /*if (head == null) return head;      
        ListNode fakeHead = new ListNode(-1);
        fakeHead.next = head;
        ListNode curr = fakeHead, prev = head;
        while (prev != null) {
            if (prev.val == val)
                curr.next = prev.next;
            else
                curr = curr.next;
            prev = prev.next;
        }
        return fakeHead.next;*/
    }
```
2. 外国高票回答，这个递归真的nice！
```javscript
public ListNode removeElements(ListNode head, int val) {
        if (head == null) return null;
        head.next = removeElements(head.next, val);
        return head.val == val ? head.next : head;
}
```
利用递归来存储中间变量，很好。但是评论区，也有说，递归太深，可能无法通过。但是也不失为一种很好的解法。
3.
```javascript
public ListNode removeElements(ListNode head, int val) {
        ListNode fakeHead = new ListNode(-1);
        fakeHead.next = head;
        ListNode curr = head, prev = fakeHead;
        while (curr != null) {
            if (curr.val == val) {
                prev.next = curr.next;
            } else {
                prev = prev.next;
            }
            curr = curr.next;
        }
        return fakeHead.next;
    }
```
