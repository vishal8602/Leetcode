### 2046.Sort-Linked-List-Already-Sorted-Using-Absolute-Values

本题的突破点在于，我们可以发现所有的正数都是从小到大排列的，所有的负数也是从大到小排列的。我们把所有的正数、负数节点分别拿出来组成两个链表，显然只需要把负数链表反转再接上正数链表就是答案了。

这种“按照绝对值升序排列”的序列有很多有意思的题目。比如说，在这样的一个数组里，能否用o(N)的时间判断是否存在two sum等于target。
