

## R: [Introduction to Java 8 Parallel Stream — Java2Blog](https://medium.com/javarevisited/java-8-parallel-stream-java2blog-e1254e593763). 
1. 这篇文章讲到了java并行流，比较了单线程运行和多线程运行。
2. 并不是都要用并行流，提到要用的情况：
+ You have a large dataset to process.
+ As you know that Java uses ForkJoinPool to achieve parallelism, ForkJoinPool forks sources stream and submit for execution, so your source stream should be splittable.
For example:
ArrayList is very easy to split, as we can find a middle element by its index and split it but LinkedList is very hard to split and does not perform very well in most of the cases.
+ You are actually suffering from performance issues.
+ You need to make sure that all the shared resources between threads need to be synchronized properly otherwise it might produce unexpected results.
