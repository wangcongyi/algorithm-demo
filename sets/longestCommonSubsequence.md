###

```

最长公共子序列  

最长公共子序列（LCS）问题是在一组序列（通常只有两个序列）中找到所有序列共有的最长子序列的问题  
它不同于最长公共子字符串不同 子序列不需要占据原始序列中的连续位置

比如:
LCS for input Sequences ABCDGH and AEDFHR is ADH of length 3
LCS for input Sequences AGGTAB and GXTXAYB is GTAB of length 4

````


```js

const longestCommonSubsequence = (set1, set2) => {
  const lcsMatrix = Array(set2.length + 1).fill(null).map(() => Array(set1.length + 1).fill(null))

  for (let columnIndex = 0; columnIndex <= set1.length; columnIndex += 1) {
    lcsMatrix[0][columnIndex] = 0
  }

  for (let rowIndex = 0; rowIndex <= set2.length; rowIndex += 1) {
    lcsMatrix[rowIndex][0] = 0
  }

  for (let rowIndex = 1; rowIndex <= set2.length; rowIndex += 1) {
    for (let columnIndex = 1; columnIndex <= set1.length; columnIndex += 1) {
      if (set1[columnIndex - 1] === set2[rowIndex - 1]) {
        lcsMatrix[rowIndex][columnIndex] = lcsMatrix[rowIndex - 1][columnIndex - 1] + 1
      } else {
        lcsMatrix[rowIndex][columnIndex] = Math.max(
          lcsMatrix[rowIndex - 1][columnIndex],
          lcsMatrix[rowIndex][columnIndex - 1],
        )
      }
    }
  }

  if (!lcsMatrix[set2.length][set1.length]) {
    return ['']
  }

  const longestSequence = []
  let columnIndex = set1.length
  let rowIndex = set2.length

  while (columnIndex > 0 || rowIndex > 0) {
    if (set1[columnIndex - 1] === set2[rowIndex - 1]) {
      longestSequence.unshift(set1[columnIndex - 1])
      columnIndex -= 1
      rowIndex -= 1
    } else if (lcsMatrix[rowIndex][columnIndex] === lcsMatrix[rowIndex][columnIndex - 1]) {
      columnIndex -= 1
    } else {
      rowIndex -= 1
    }
  }

  return longestSequence
}

```
