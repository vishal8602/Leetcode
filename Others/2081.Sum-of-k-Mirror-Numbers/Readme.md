### 2081.Sum-of-k-Mirror-Numbers

本题本质就是从小到大枚举10进制和k进制都是回文形态的数。对于关于回文数的题目，最常见的做法就是枚举。类似的题目还有479，866，906。

对于任何十进制的数字xyz，我们只要翻转一下，就能得到两种回文数，xyzyx和xyzzyx。并且我们发现，对于从小到大的xyz，我们所构造的回文数也一定是从小到大递增的。更具体的说，我们从小到大遍历所有的xyz，那么就能得到从小到大所有的五位数的回文数xyzyx，同时还可以得到从小到大所有的六位数的回文数xyzzyx。依次类推。所以我们本质上就得到了所有从小到大所有的十进制回文数，只需再检查一下他们在k进制形态下是否是回文即可。

那么我们是否可以反过来做，遍历所有从小到大的k进制回文数，再查验是否是十进制回文数呢？理论上可以的：你先从小到大生成10进制数、再转为k进制数、再镜像翻转。 但是有点需要思考的地方。因为k小于10，遍历k进制回文数的效率不及遍历十进制回文数的效率高。k越小，在相同范围内，k进制的数字就越长，回文数概率就越高。比如十进制的两位数，只有11-99这9种回文数。但是对应的二进制表示却是从1010到1100011：期间有（部分）四位数的回文、（任意）五位数的回文、（任意）六位数的回文、（部分）七位数的回文。显然，在需要满足既是k进制回文、又是10进制回文的前提下，我们遍历10进制回文数需要尝试的次数更少。

此外还有一个具体的实现细节。如何高效实现镜像翻转？即如何由xyz得到zyx？不要用数组来拆解每一个digit，用如下的数学方法：
```cpp
LL reverse(LL a)
{
    LL b = 0;
    while (a>0)
    {
       b = b*10 + a%10;
       a /= 10;
    }
    return b;
}
```
