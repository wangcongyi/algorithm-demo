#### 组合总和

```

定一个无重复元素的数组 candidates 和一个目标数 target ，
找出 candidates 中所有可以使数字和为 target 的组合
candidates 中的数字可以无限制重复被选取

输入: candidates = [2,3,5], target = 8,
所求解集为:[ [2,2,2,2], [2,3,3], [3,5] ]

```

```js

const combinationSum = (
  candidates,
  remainingSum,
  finalCombinations = [],
  currentCombination = [],
  startFrom = 0,
) => {
  if (remainingSum < 0) {
    return finalCombinations
  }

  if (remainingSum === 0) {
    finalCombinations.push(currentCombination.slice())
    return finalCombinations
  }

  for (let candidateIndex = startFrom; candidateIndex < candidates.length; candidateIndex += 1) {
    const currentCandidate = candidates[candidateIndex]
    currentCombination.push(currentCandidate)
    combinationSum(
      candidates,
      remainingSum - currentCandidate,
      finalCombinations,
      currentCombination,
      candidateIndex,
    )
    currentCombination.pop()
  }
  return finalCombinations
}

```
