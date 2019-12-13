### 选择性排序

```

线性搜索数列并找到最小值 将最小值替换到左端的的数字
重复相同的操作....

```

![选择性排序](https://github.com/wangcongyi/learning-algorithm/blob/master/images/selectionSort.gif)


```js

const selectionSort = arr => {
  let len = arr.length
  let temp, minIndex
  for (let i = 0; i < len - 1; i++) {
    for (let j = i + 1; j < len; j++) {
      minIndex = i
      if (arr[minIndex] > arr[j]) {
        minIndex = j
      }
      if (minIndex !== i) {
        temp = arr[i]
        arr[i] = arr[minIndex]
        arr[minIndex] = temp
      }
    }
  }
}

```
