### 2050.Parallel-Courses-III

本题本质是求有向无环图里的最长路径。图论里有各种基于松弛的算法，但是本题最容易理解的其实就是拓扑排序。

对于任何一门课程a，它的最早完成时间t(a)取决于它的所有先修课程的完成时间里最长的那个，即```t(a) = max{t(bi)+time[a]}```，其中bi是a的先修课程。因为本题给出的是有向无环图，所以不会有循坏依赖，即t(bi)不会依赖于t(a)本身。那么我们什么时候知道可以t(a)更新完毕了呢？很简单，只要每确定了一个t(bi)，我们就把a的入度减一。当发现a的入度为0时，说明t(a)已经被更新完毕。

实现拓扑排序一般会用BFS。队列初始时刻加入那些入度为0的课程。每次弹出一门课程，它的所以后续课程就有机会更新一次。发现某个后续课程的入度减至了零，说明它的所有先修课程已经都确定了，那么这么后续课程也就确定了，就可以加入队列。

本题输出的结果是所有课程的完成时刻里的最大值。
