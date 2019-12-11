### 排列

```

无序 我们叫 组合
有序 我们叫 排列

```

![permutation](https://github.com/wangcongyi/learning-algorithm/blob/master/images/x.png)

```js

// 排列不可以重复的情况
// 相当于各个元素存在 竞态 某个元素不能同时出现两个位置
// 总共有 n! 种可能

const permutateWithoutRepetitions = (permutationOptions) => {
  if (permutationOptions.length === 1) {
    return [permutationOptions]
  }

  const permutations = []
  const smallerPermutations = permutateWithoutRepetitions(permutationOptions.slice(1))
  const firstOption = permutationOptions[0]

  for (let permIndex = 0; permIndex < smallerPermutations.length; permIndex += 1) {
    const smallerPermutation = smallerPermutations[permIndex]
    for (let positionIndex = 0; positionIndex <= smallerPermutation.length; positionIndex += 1) {
      const permutationPrefix = smallerPermutation.slice(0, positionIndex)
      const permutationSuffix = smallerPermutation.slice(positionIndex)
      permutations.push(permutationPrefix.concat([firstOption], permutationSuffix))
    }
  }

  return permutations
}

console.log(permutateWithoutRepetitions([0, 1, 2, 3]))

/////////////////////////////////////
// 排列可以重复的情况
// 相当于 自行车的锁 我的是 五位  每位 0-9 个数  总共有 10^5 = 10000 个可能

const permutateWithRepetitions = (permutationOptions, permutationLength = permutationOptions.length) => {
  if (permutationLength === 1) {
    return permutationOptions.map(permutationOption => [permutationOption])
  }

  const permutations = []

  const smallerPermutations = permutateWithRepetitions(
    permutationOptions,
    permutationLength - 1,
  )

  permutationOptions.forEach((currentOption) => {
    smallerPermutations.forEach((smallerPermutation) => {
      permutations.push([currentOption].concat(smallerPermutation))
    })
  })

  return permutations
}

console.log(permutateWithRepetitions([0, 1, 2, 3, 4, 5, 6, 7, 8, 9], 5))

```
