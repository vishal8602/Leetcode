### 1969.Minimum-Non-Zero-Product-of-the-Array-Elements

我们首先发现，无论如何交换1的位置，这些数字的和是不变的，无非就是“某位上的bit 1从这个数字跑到了那个数字”而已，每个1代表的实际大小没有变化。根据“差大积小”的直觉，对于固定的元素总和，我们尽量采用极端分解出一大一小的分解策略，来使得乘积最小。比如说sum=6时，拆分为```0*6```的乘积要小于```1*5```的乘积，小于```2*4```的乘积，小于```3*3```的乘积。

在本题中，我们最先思考的就是将所有的bit 1都集中到一起得到尽量大的数，剩下的数自然就会极端的小。这样就可以将原先的数字重组为 2^(p-1)个```111...111```和 2^(p-1)-1个```000...000```。

但是题目要求不能构造0，所以我们退而求次，构造尽量多的1. 很明显，我们将前者拿出 2^(p-1)-1个```1```出来给后者，这样我们就得到了这样一个组合：1个```111...111```，2^(p-1)-1个```111...110```，2^(p-1)个```000...001```。第一部分已经是最大了，第三部分已经是最小了，第二部分也无法再做任何“差大积小”的重组（高位的1都塞满了无法挪动），因此这套组合就是最优答案。

本题的C++代码中需要用到快速幂。另外记得base需要取模（将数值范围降到INT32，否则两个Long Long的乘积会溢出），但是指数不能取模。
