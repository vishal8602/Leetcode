### 2056.Number-of-Valid-Move-Combinations-On-Chessboard

首先这道题的题意描述比较迷惑。本质上是，确定了每个棋子的移动方向之后，每一个回合，所有的棋子都必须朝各自约定的方向移动一步（除非它决定以后不再移动）。走多少个回合不限，但约束是所有的棋子不能碰撞或者出界。问盘面上有多少种棋子摆放的组合。

此时再看这道题，思路就会清晰很多。因为只有最多四个棋子，里面只有最多一个皇后，所以方向组合的可能性只有```4*4*4*8=512```种，似乎可以枚举考虑。

在固定了所有棋子的各自方向之后，我们就模拟他们共同前进的轨迹。在每一个回合，我们都需要考虑其中某些棋子停止前进的情况。很想然，停止前进（或者继续前进）的棋子必然是上一个回合前进的棋子的子集，所以这就是一个遍历子集的问题。具体的说，我们在刚出发的时候标注1111，表示所有棋子都可以前进。在第一个回合的时候，有些棋子可能就不走了（认为已经到了它的终点），能继续走的就有```2^4-1=15```种情况，即可以写成1111,1110,1101,1011,0111,1100,1001,0011... 有了这个状态变量，我们就可以在推进的时候，时刻知道哪些棋子可以继续走下去。比如说0110，那么我们就只对第2和第3个棋子在它们的方向上加1. 有了棋子们的新位置和新状态，就可以继续递归下去。

递归的终结就是：任意两个棋子相撞了，或者任意一个棋子出界了。

最终的答案是把盘面上所有出现的棋子位置组合都统计。这里需要特别注意，我们需要hash来去重。不是说每次走到一个新的棋子组合都是unique的。这是因为有一类特殊的情况。假设“A向上走0步，B向右走一步”，等同于“A向下走0步，B向右走一步”。这两种前进模式是出现在两个不同的方向组合里面的，我们在某个方向组合的DFS过程中无法避免，必须靠全局的去重。

因为棋子的数目比较少，盘面也不大，Hash的方法可以就是将所有棋子的坐标拼接起来。

另外一个优化的地方，Hash不仅可以去重，而且可以避免重复搜索。还是上面的例子，“A向上走0步，B向右走一步”及其后续都被探访过之后，那么“A向下走0步，B向右走一步”及其后续就是一模一样的路径了。这是因为在两种情况里，A都约定不再移动。
