### 2242.Maximum-Score-of-a-Node-Sequence

因为题目需要找的序列只有四个节点、三条边，所以我们可以通过穷举中间的边，来暴力枚举所有的节点组合。

比如，如果我们考察以(a,b)为中间的边，那么我们接下来就要找a的一个邻接节点i，b的一个邻接节点j，组成i-a-b-j的序列。为了使得节点的score总和最大，原则上贪心地找a的最大邻居、b的最大邻居。但是容易想到会有一些特殊情况，比如a的最大邻居恰好是b或者j的话，我们就无法保证这个序列的四个节点是互异的。同理，b的最大邻居也有这样的问题。

那么我们是否该枚举所有a的邻居与b的邻居的组合，考察所有可能的{i,j}再取最大值吗？其实不必。根据之前的分析，我们只需要考察a的最大的三个邻居即可，这样就一定能找到一个不与b和j重复的。同理，我们也只保留b的最大的三个邻居。这样，最多9组配对，必然可以找到一组互异的i-a-b-j，我们取其中的最大值即可。

本题的时间复杂度就是```o(ElogE + 9*E)```
