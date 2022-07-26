### 2088.Count-Fertile-Pyramids-in-a-Land

如果我们想不重复地数金字塔，那么就必须抓住金字塔的特征。我们通过数特征来统计金字塔的数目。

我们最容易想到的是金字塔的顶尖。任何一个金字塔都有一个唯一的顶尖，我们可以考虑遍历每个格子，思考如果它作为某个金字塔的顶尖的话，可以代表哪些金字塔。显然，我们光看这个格子A本身是不充分，我们得看它往下一格B，查看B是否为一个长度为3的区间的中点；再查看B的下一格C，查看C是否为一个长度为5的区间的中点... 直至类似的规律不能再持续下去。我们往下几行，就意味着A可以是几个不同金字塔的塔尖。不过这样的时间复杂度将会是o(MMN).

我们注意到，上述方法时间复杂度高是因为我们站在top，无法了解bottom的情况，所以才需要逐层下沉去调查。举个例子，我们知道某点A是一个三层金字塔的顶，那么它是否也是一个四层金字塔的顶呢？我们不知道，得下沉了才知道。

那么反过来会怎么样呢？我们站在下层，是否能知道上层的情况呢？这其实是可行的。比如说，我们站在某点A，如果知道它是一个三层金字塔的底座中点，那么我们就一定知道A也同时是一个二层金子它的底座中点。这样，如果考察每个点作为金字塔底座中点的情况，那么我们就不需要向上调查就能知道它可以对应几个不同的金字塔。这就方便多了。

那么对于任意一点A，我们如何可以知道它最大可以是多少层金字塔的底座中点呢？首先，我们要知道它自身可以是一个多长连续区间的中点。这个可以通过从左往右、从右往左两遍预处理得到。其次我们知道，如果A想成为一个三层金字塔的底座中点，那么A上面的那个格子B必须至少是一个两层金字塔的底座中点。所以我们对于A对应底座半径就有了如下的表达式：
```
dp(A) = min(left(A), right(A), dp(B)+1)
```
其中dp表示最大金字塔的底座半径，left表示A往左边最多连续多少个1，right表示A往右边最多连续多少个1.

注意最终答案不能包括层数为1的金字塔，所以答案是累加所有格子的dp值减1.
