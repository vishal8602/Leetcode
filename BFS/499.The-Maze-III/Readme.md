### 499.The-Maze-III

此题在505.The-Maze-II的基础上增加了一个条件：在最短距离相同的情况下，要更新为字典序最小的指令。

事实上本题与505并没有太大的区别，只不过优先队列的比较函数里增加一个条件：当（离源点）路径距离相等的时候，将路径指令的字典序更小的节点排在更前面。这样当终点第一次从优先队列里弹出的时候，不仅对应的距离最短，而且如果有多个相同距离的路径的话，指令也是最小的。

有人会疑问，当终点第一次从队列里弹出的时候，固然对应着距离最短的路径，那么怎么保证所有该有着相同最短距离、但指令不同的路径都已经进入队列了呢？这是因为，假设终点第一次弹出队列所对应的路径长度是x，那么此时所有路径长度小于x的路径必然已经都弹出队列了，他们的后续路径必然包括了所有以距离x达到终点的路径。
