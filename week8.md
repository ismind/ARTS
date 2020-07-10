## A: [剑指 Offer 22. 链表中倒数第k个节点](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)
输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。例如，一个链表有6个节点，从头节点开始，它们的值依次是1、2、3、4、5、6。这个链表的倒数第3个节点是值为4的节点。
#### 示例：
> 给定一个链表: 1->2->3->4->5, 和 k = 2.
> 返回链表 4->5.
1. 首先，这道题我真的没有看懂什么意思，没关系，先在代码离写一句，然后更改测试案例，这样来理解题目的意思。
```javascript
   return null
```
2. 理解了题目的意思，就开始动手了。自己的代码改了几次。
```javascript
   public ListNode getKthFromEnd(ListNode head, int k) {
       if (head == null) return null;
       ListNode first = head, last = head.next;
       int index = 1;
       while (last != null) {
           last = last.next;
           index++;
       }
       if (k > index) return null;
       //System.out.println(index);
       int move = index - k;
       //System.out.println(move);
       while (move > 0) {
           first = first.next;
           move--;
       }  
       return first;
    }
```
3. 公众号的解答比我的更好(https://mp.weixin.qq.com/s/_PjbCBBB2g33GO5jFm4DYQ)
```javascript
public ListNode getKthFromEnd(ListNode head, int k) {
        //初始化两个指针 former 和 latter，一开始都指向链表的头节点
        ListNode former = head, latter = head;
        //前指针 former 先向前走 k 步
        for(int i = 0; i < k; i++){
            former = former.next;
        }
        // 两个指针 former 和 latter 同时向前移动，直到前指针 former 指向 NULL
        while(former != null) {
            former = former.next;
            latter = latter.next;
        }
        //最后返回 latter 
        return latter;
    }
```

## R: [Introduction to Java 8 Parallel Stream — Java2Blog](https://medium.com/javarevisited/java-8-parallel-stream-java2blog-e1254e593763). 
1. 这篇文章讲到了java并行流，比较了单线程运行和多线程运行。
2. 并不是都要用并行流，提到要用的情况：
+ You have a large dataset to process.
+ As you know that Java uses ForkJoinPool to achieve parallelism, ForkJoinPool forks sources stream and submit for execution, so your source stream should be splittable.
For example:
ArrayList is very easy to split, as we can find a middle element by its index and split it but LinkedList is very hard to split and does not perform very well in most of the cases.
+ You are actually suffering from performance issues.
+ You need to make sure that all the shared resources between threads need to be synchronized properly otherwise it might produce unexpected results.

###  [Asynchronous Programming In Java](https://medium.com/swlh/asynchronous-programming-in-java-d4390cceea3a). 
+ 这篇文章主要讲了Spring webFlux module的一些方法实现异步编程。
