### 快速排序

```

通过一趟排序将待排记录分隔成独立的两部分
其中一部分记录的关键字均比另一部分的关键字小
则可分别对这两部分记录继续进行排序，以达到整个序列有序

```

```js

const quickSort = (arr) => {
  if (arr.length <= 1) {
    return arr
  }
  const pivotIndex = Math.floor(arr.length / 2)
  const pivot = arr.splice(pivotIndex, 1)[0]
  const left = []
  const right = []
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] < pivot) {
      left.push(arr[i])
    } else {
      right.push(arr[i])
    }
  }
  return quickSort(left).concat([pivot], quickSort(right))
}

```
