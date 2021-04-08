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

### 最小公倍数

```

两个或多个整数公有的倍数叫做它们的公倍数  
其中除0以外最小的一个公倍数就叫做这几个整数的最小公倍数

两个数的乘积等于 两个数的最大公约数乘以最小公倍数
所以 一般计算 两个数 最小公倍数的时候 可以运用 lcm(a, b) = a * b / gcd(a, b)

```

```js

const leastCommonMultiple = (a, b) => {
  return ((a === 0) || (b === 0)) ? 0 : Math.abs(a * b) / euclidean(a, b);
}

```
