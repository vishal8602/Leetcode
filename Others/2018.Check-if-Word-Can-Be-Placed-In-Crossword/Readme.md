### 2018.Check-if-Word-Can-Be-Placed-In-Crossword

此题就是暴力搜索。

搜索的关键是找一个起点格子和方向。起点给子的要求是：1. 靠着边界或者一个#符号。2. 格子本身是空格或者word[0]. 3. 在条件1的反方向一侧是我们的尝试匹配的方向。

匹配的要求是：1. 一路所经过的格子恰好是word，允许其中有空格。2. 匹配完之后再走一步的话，必须是边界或者一个#符号。

了解了这些要求之后，代码就不难写了。
