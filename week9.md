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

## R: [The Future of the Web Is Here Already](https://medium.com/tech-explained/the-future-of-the-web-is-here-already-20065e3049af) 
1. 这篇文章主要介绍了PWA，这种新的app模式。
2. 我个人觉得这是一种趋势，想要一个应用，还需要下载，不如直接打开一个网页更方便。
3. 其实，上次做胃镜时，就在想，未来可不可以不需要一根管子伸到胃里，直接有个什么仪器在外面一扫描就可以知道胃部有什么问题呢？
4. 以后的app会不会都是一个个网页呢？需要哪个直接打开对应的网页就好了。

## T:
最近在学习vue，其中几点收获：
1. vue是采用MVVM模式，只需要关注数据就可以了。
2. 就是vue的语法与一些细节，然后就是，觉得初学看视频确实很容易入门，我自己是花了RMB买的视频，个人还是觉得值得的。
