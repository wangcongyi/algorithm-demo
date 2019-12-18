#### 莱文斯坦距离

```

莱文斯坦距离是用于测量两个序列之间差异的字符串量度
将一个字符串转换为另一个字符串所需的最小单字符编辑（插入，删除或替换）次数。

```

![莱文斯坦距离](https://github.com/wangcongyi/learning-algorithm/blob/master/images/levenshtein.png)

```js

const levenshteinDistance = (a, b) => {
  const distanceMatrix = Array(b.length + 1).fill(null).map(() => Array(a.length + 1).fill(null))
  for (let i = 0; i <= a.length; i += 1) {
    distanceMatrix[0][i] = i
  }
  for (let j = 0; j <= b.length; j += 1) {
    distanceMatrix[j][0] = j
  }

  for (let j = 1; j <= b.length; j += 1) {
    for (let i = 1; i <= a.length; i += 1) {
      const indicator = a[i - 1] === b[j - 1] ? 0 : 1
      distanceMatrix[j][i] = Math.min(
        distanceMatrix[j][i - 1] + 1, // deletion
        distanceMatrix[j - 1][i] + 1, // insertion
        distanceMatrix[j - 1][i - 1] + indicator, // substitution
      )
    }
  }

  return distanceMatrix[b.length][a.length]
}

```
