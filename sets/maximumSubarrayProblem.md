### 最大子数字问题

```

最大子数组是指： 在一个数组中 找到最大和的子数组

```

![最大子数组](https://github.com/wangcongyi/learning-algorithm/blob/master/images/m.png)


```js

// Brute Force solution
// Complexity: O(n^2)
const bfMaximumSubarray = inputArray => {
  let maxSubarrayStartIndex = 0
  let maxSubarrayLength = 0
  let maxSubarraySum = null
  for (let startIndex = 0; startIndex < inputArray.length; startIndex += 1) {
    let subarraySum = 0
    for (let arrLength = 1; arrLength <= (inputArray.length - startIndex); arrLength += 1) {
      subarraySum += inputArray[startIndex + (arrLength - 1)]
      if (maxSubarraySum === null || subarraySum > maxSubarraySum) {
        maxSubarraySum = subarraySum
        maxSubarrayStartIndex = startIndex
        maxSubarrayLength = arrLength
      }
    }
  }
  return inputArray.slice(maxSubarrayStartIndex, maxSubarrayStartIndex + maxSubarrayLength)
}

///////////////////////////////////
// Dynamic Programming solution
// Complexity: O(n)
const dpMaximumSubarray = inputArray => {
  let maxSum = -Infinity
  let currentSum = 0
  let maxStartIndex = 0
  let maxEndIndex = inputArray.length - 1
  let currentStartIndex = 0
  inputArray.forEach((currentNumber, currentIndex) => {
    currentSum += currentNumber
    if (maxSum < currentSum) {
      maxSum = currentSum
      maxStartIndex = currentStartIndex
      maxEndIndex = currentIndex
    }
    if (currentSum < 0) {
      currentSum = 0
      currentStartIndex = currentIndex + 1
    }
  })
  return inputArray.slice(maxStartIndex, maxEndIndex + 1)
}

```
