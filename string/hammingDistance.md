#### 汉明距离

```

两个整数之间的汉明距离指的是这两个数字对应二进制位不同的位置的数目
两个字符串之间的汉明距离是相应符号不同的位置数
换句话说，它测量将一个字符串转换为另一个字符串所需的最小替换数，或可能将一个字符串转换为另一个字符串的最小错误数
在更一般的上下文中，汉明距离是用于测量两个序列之间的编辑距离的几个字符串指标之一

```

```js

const numberHammingDistance = (a, b) => {
  let d = 0
  let h = a ^ b
  while (h > 0) {
    d++
    h &= h - 1
  }
  return d
}

const StringHammingDistance = (a, b) => {
  if (a.length !== b.length) {
    throw new Error('Strings must be of the same length')
  }

  let distance = 0

  for (let i = 0; i < a.length; i += 1) {
    if (a[i] !== b[i]) {
      distance += 1
    }
  }

  return distance
}

```
