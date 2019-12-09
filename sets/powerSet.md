### 集合的幂集

```

集合的幂集 就是原集合中所有的子集（包括全集和空集）构成的集族

```

![集合的幂集](https://github.com/wangcongyi/learning-algorithm/blob/master/images/c.svg)

可以根据 **2进制** 的思路求解

||abc|subset|
|---|---|---|
| 0 | 000 | {}        |
| 1 | 001 | {c}       |
| 2 | 010 | {b}       |
| 3 | 011 | {b, c}    |
| 4 | 100 | {a}       |
| 5 | 101 | {a, c}    |
| 6 | 110 | {a, b}    |
| 7 | 111 | {a, b, c} |


```js

const btPowerSet = (originalSet, allSubsets = [[]], currentSubSet = [], startAt = 0) => {

  for (let position = startAt; position < originalSet.length; position += 1) {
    currentSubSet.push(originalSet[position])
    allSubsets.push([...currentSubSet])
    btPowerSet(originalSet, allSubsets, currentSubSet, position + 1)
    currentSubSet.pop()
  }

  return allSubsets
}

```
