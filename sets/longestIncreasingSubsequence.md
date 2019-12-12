### 最长递增子序列

```

增长最快的子序列问题是找到给定序列的子序列 
其中子序列的元素按从小到大的顺序排列，并且子序列越长越好 
此子序列不一定是连续的或唯一的
比如 

0, 8, 4, 12, 2, 10, 6, 14, 1, 9, 5, 13, 3, 11, 7, 15 最长递增子序列

0, 2, 6, 9, 11, 15
0, 4, 6, 9, 11, 15
0, 2, 6, 9, 13, 15
......

```



```js

const dpLongestIncreasingSubsequence = sequence => {
  const lengthsArray = Array(sequence.length).fill(1)

  let previousElementIndex = 0
  let currentElementIndex = 1

  while (currentElementIndex < sequence.length) {
    if (sequence[previousElementIndex] < sequence[currentElementIndex]) {
      const newLength = lengthsArray[previousElementIndex] + 1
      if (newLength > lengthsArray[currentElementIndex]) {
        lengthsArray[currentElementIndex] = newLength
      }
    }

    previousElementIndex += 1
    if (previousElementIndex === currentElementIndex) {
      currentElementIndex += 1
      previousElementIndex = 0
    }
  }
  let longestIncreasingLength = 0

  for (let i = 0; i < lengthsArray.length; i += 1) {
    if (lengthsArray[i] > longestIncreasingLength) {
      longestIncreasingLength = lengthsArray[i]
    }
  }

  return longestIncreasingLength
}


```
