### 组合

```

无序 我们叫 组合
有序 我们叫 排列

```

![combinations](https://github.com/wangcongyi/learning-algorithm/blob/master/images/y.png)


```js


// 组合可以重复元素

const combineWithRepetitions = (comboOptions, comboLength) => {
  if (comboLength === 1) {
    return comboOptions.map(comboOption => [comboOption])
  }

  const combos = []
  comboOptions.forEach((currentOption, optionIndex) => {
    const smallerCombos = combineWithRepetitions(
      comboOptions.slice(optionIndex),
      comboLength - 1,
    )

    smallerCombos.forEach((smallerCombo) => {
      combos.push([currentOption].concat(smallerCombo))
    })
  })

  return combos
}


// 组合不可以重复元素

const combineWithoutRepetitions = (comboOptions, comboLength) => {
  if (comboLength === 1) {
    return comboOptions.map(comboOption => [comboOption])
  }
  const combos = []

  comboOptions.forEach((currentOption, optionIndex) => {
    const smallerCombos = combineWithoutRepetitions(
      comboOptions.slice(optionIndex + 1),
      comboLength - 1,
    )

    smallerCombos.forEach((smallerCombo) => {
      combos.push([currentOption].concat(smallerCombo))
    })
  })

  return combos
}


```
