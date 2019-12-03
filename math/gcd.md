### 最大公约数

```

计算两个数字的最大公约数 ( greatest common divisor ) 的有效方法  
欧几里得算法又叫辗转相除法   
更相减损法

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
