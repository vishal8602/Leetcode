### 1963.minimum-number-of-swaps-to-make-the-string-balanced

本题的关键点是要想到，如果把所有能就近配对的括号都消去的话，剩余的括号必然是形如```]]]][[[[[```的模式。这些位于两边的括号是无论如何都无法在原字符串里被匹配的。

对于连续n个右括号+连续n个左括号，需要多少次swap能够让他们配对呢？我们不妨多尝试几个例子：
```
][: => [] 1 swap
]][[: => [][] 1 swap
]]][[[: => []][[] => [][][] 2 swaps
]]]][[[[: => []]][[[] => [][][][] 2 swaps
```
所以我们可以总结出规律来，只需要(n+1)/2次交换。

