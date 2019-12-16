### 归并排序

```

归并排序是建立在归并操作上的一种有效的排序算法
将已有序的子序列合并，得到完全有序的序列
即先使每个子序列有序，再使子序列段间有序
若将两个有序表合并成一个有序表，称为2-路归并

```

![归并排序](https://github.com/wangcongyi/learning-algorithm/blob/master/images/mergeSort.gif)

```js

const mergeSort = arr => {
  const len = arr.length
  if (len < 2) {
    return arr
  }
  const middle = Math.floor(len / 2),
    left = arr.slice(0, middle),
    right = arr.slice(middle)


  const _merge = (left, right) => {
    let result = []

    while (left.length && right.length) {
      if (left[0] <= right[0]) {
        result.push(left.shift())
      } else {
        result.push(right.shift())
      }
    }

    while (left.length)
      result.push(left.shift())

    while (right.length)
      result.push(right.shift())

    return result
  }

  return _merge(mergeSort(left), mergeSort(right))
}


```
