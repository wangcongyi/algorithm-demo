### 最短公共父序列

```

两个序列X和Y的最短公共超序列（SCS）是具有X和Y作为子序列的最短序列
换句话说，假设我们得到了两个字符串str1和str2，找到同时具有str1和str2作为子序列的最短字符串

```


```js

// longestCommonSubsequence 为 最长公共子序列方法

const shortestCommonSuperSequence = (set1, set2) => {
  const lcs = longestCommonSubsequence(set1, set2)
  if (lcs.length === 1 && lcs[0] === '') {
    return set1.concat(set2)
  }
  let supersequence = []

  let setIndex1 = 0
  let setIndex2 = 0
  let lcsIndex = 0
  let setOnHold1 = false
  let setOnHold2 = false

  while (lcsIndex < lcs.length) {
    if (setIndex1 < set1.length) {
      if (!setOnHold1 && set1[setIndex1] !== lcs[lcsIndex]) {
        supersequence.push(set1[setIndex1])
        setIndex1 += 1
      } else {
        setOnHold1 = true
      }
    }

    if (setIndex2 < set2.length) {
      if (!setOnHold2 && set2[setIndex2] !== lcs[lcsIndex]) {
        supersequence.push(set2[setIndex2])
        setIndex2 += 1
      } else {
        setOnHold2 = true
      }
    }

    if (setOnHold1 && setOnHold2) {
      supersequence.push(lcs[lcsIndex])
      lcsIndex += 1
      setIndex1 += 1
      setIndex2 += 1
      setOnHold1 = false
      setOnHold2 = false
    }
  }

  if (setIndex1 < set1.length) {
    supersequence = supersequence.concat(set1.slice(setIndex1))
  }

  if (setIndex2 < set2.length) {
    supersequence = supersequence.concat(set2.slice(setIndex2))
  }

  return supersequence
}

```
