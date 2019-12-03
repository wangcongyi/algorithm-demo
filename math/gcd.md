### 最大公约数

```

计算两个数字的最大公约数 ( greatest common divisor ) 的有效方法  
欧几里得算法又叫辗转相除法   
更相减损法

更相减损术和辗转相除法的主要区别在于前者所使用的运算是“减” 后者是“除”  
从算法思想上看两者并没有本质上的区别 但如果遇到一个数很大 另一个数比较小的情况  
可能要进行很多次减法才能达到一次除法的效果  
从而使得算法的时间复杂度退化为 O(N) 辗转相除法的时间复杂度稳定于 O(logN)

```

```js

const euclidean = (num1, num2) => {
  const a = Math.abs(num1)
  const b = Math.abs(num2)

  return (b === 0) ? a : euclidean(b, a % b)
}

//////////
const euclidean = (num1, num2) => {
  let a = Math.abs(num1)
  let b = Math.abs(num2)

  while (a && b && a !== b) {
    [a, b] = a > b ? [a - b, b] : [a, b - a]
  }

  return a || b
}

```
