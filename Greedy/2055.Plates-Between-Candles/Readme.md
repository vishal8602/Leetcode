### 2055.Plates-Between-Candles

很显然，对于给定的区间[a,b]里，我希望知道a右边最近的蜡烛位置x，和b左边最近的蜡烛位置y。显然，我们可以用状态机的思想提前准备好next和last数组。next[i]表示i的下一个（可以是自身）出现蜡烛的位置；last[i]表示i的前一个（可以是自身）出现蜡烛的位置。这些都可以用o(n)实现。

知道了x和y，想求区间[x,y]内的盘子数量，显然用前缀和最方便。
