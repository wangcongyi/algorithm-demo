### 希尔排序

```

希尔排序也称增量递减排序算法 即跨多步版的 insertionSort
insertionSort 可以看作 ShellSort 中 gap=1 的特例

```

```js

const shellSort = arr => {
  for (let gap = Math.floor(arr.length / 2); gap > 0; gap = Math.floor(gap / 2)) {
    for (let i = gap; i < arr.length; i++) {
      let j = i
      const current = arr[i]
      while (j - gap >= 0 && current < arr[j - gap]) {
        arr[j] = arr[j - gap]
        j = j - gap
      }
      arr[j] = current
    }
  }
  return arr
}

```
