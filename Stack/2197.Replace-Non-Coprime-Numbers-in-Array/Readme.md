### 2197.Replace-Non-Coprime-Numbers-in-Array

这道题出得很精彩。通常的套路是，如果想合并若干个相邻的元素，可以考虑栈。如果想合并不相邻的元素（归为一类），那么可以考虑并查集。

在本题中，每加入一个新元素，我们自然会考虑是否与数组前一个元素互质。如果新元素与前一个元素互质，那么就只能保留。如果不是那么就可以马上合并成为他们的最大公约数（LCM），因为越大的数（即因数越多的数）越容易与其他数字合并。特别注意，合并之后我们还可以持续考察它是否能与再之前的元素合并，比如这个例子```3,2,6```，第二个数2是与第一个数3互质的，但是当第三个数字6出现后，第二个数和第三个数合并成6之后，就可以往前再合并3. 用这个方法就可以把所有相邻的、可以合并的元素都汇聚成一个。

事实上，本题上述的贪心策略就模拟了栈的基本操作。
