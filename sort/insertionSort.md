### 插入排序

```

插入排序在实现上 通常采用in-place排序（即只需用到O(1)的额外空间的排序）
因而在从后向前扫描过程中 需要反复把已排序元素逐步向后挪位 为最新元素提供插入空间

````

![插入排序](https://github.com/wangcongyi/learning-algorithm/blob/master/images/insertionSort.gif)

```js

const insertionSort = arr => {
  var len = arr.length
  var preIndex, current
  for (let i = 1; i < len; i++) {
    preIndex = i - 1
    current = arr[i]
    while (preIndex >= 0 && arr[preIndex] > current) {
      arr[preIndex + 1] = arr[preIndex]
      preIndex--
    }
    arr[preIndex + 1] = current
  }
  return arr
}

```
