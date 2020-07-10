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
4. 我又看了一下留言，果然，事情不简单！
```javascript
不少人在面试前从网上看到过这道用两个指针遍历的思路来解答这道题，因此听到面试官的这道题，他们心中一喜，很快就写出了代码。可是几天后等来的不是Offer，而是拒信，于是百思不得其解。其实原因很简单，就是自己的代码不够鲁棒。面试官可以找出3种方法让这段代码崩溃。

1、输入 Head 指针为Null。由于代码会试图访问空指针指向的内存，程序会崩溃。
2、输入以 Head 为头结点的链表的结点总数少于 k 。由于在 for 循环中会在链表向前走k-1步，仍然会由于空指针造成崩溃。
3、输入的参数 k 为 0. 或负数，同样会造成程序的崩溃。
```
5. 自己确实忽略了k的取值，考虑到了head为null，但是没有考虑k，这个算是自己的一个不足。
6. 留言区说到，面试环节很重要，要让面试官看到你的思考过程。然后说到了双指针的方法：
```javascript
代码是对的，提交过去也不会报错，只不过在面试的时候需要和面试官沟通这些异常情况怎么处理，让面试官知道你的思考过程
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
