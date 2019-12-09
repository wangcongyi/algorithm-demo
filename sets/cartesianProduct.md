### 笛卡尔乘积

![笛卡尔乘积](https://github.com/wangcongyi/learning-algorithm/blob/master/images/d.svg)

```js

const cartesianProduct = (setA = [], setB = []) => {
  const product = []

  for (let indexA = 0; indexA < setA.length; indexA += 1) {
    for (let indexB = 0; indexB < setB.length; indexB += 1) {
      product.push([setA[indexA], setB[indexB]])
    }
  }

  return product
}

```
