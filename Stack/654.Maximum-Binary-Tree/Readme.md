### 654.Maximum-Binary-Tree

#### 解法1：暴力递归
每一次遍历一段区间寻找里面的最大值，然后以其为根，左右两侧的子区间各自递归建树、并作为根的左节点和右节点。

这样的时间复杂度是Nlog(N)，其中log(N)表示树的层树。如果这个序列是递增的，那么树的层数会是o(N)，算法退化成o(N^2).

#### 解法2：单调栈
此处单调栈的用法非常巧妙，并没有相似的题目，有一定的难度。

我们维护一个单调递减的序列。我们想象一下，如果当前数组元素里都是递减的，那么他们必然组成连续的右节点的关系。OK，此时突然出现了一个较大的数A，那么A的左节点必然连接目前栈里面恰好比A小的那个元素。所以你需要不停地腾退栈顶元素，并且把最后一个恰好比A小的那个元素B接到A的左节点上。同时，A需要设置为当前栈顶元素C的右节点。如下图所示，相当于把A插入了C的右子树里，原先B子树都移到了A的左子树。这样就实现了题目所要求的目的。
```
 C       
   \     A 
     B
       \
```
最终，栈底的元素（最大值）就是全局的根节点。
