### 堆排序

```

堆排序（Heapsort）是指利用堆这种数据结构所设计的一种排序算法
堆积是一个近似完全二叉树的结构，并同时满足堆积的性质 即子结点的键值或索引总是小于（或者大于）它的父节点

```

![堆排序](https://github.com/wangcongyi/learning-algorithm/blob/master/images/heapSort.gif)

```js

const heapSort = array => {

  const _swap = (array, i, j) => {
    const temp = array[i]
    array[i] = array[j]
    array[j] = temp
  }

  const _maxHeap = (array, index, heapSize) => {
    let max, left, right
    while (true) {
      max = index
      left = 2 * index + 1
      right = 2 * (index + 1)

      if (left < heapSize && array[index] < array[left]) {
        max = left
      }

      if (right < heapSize && array[max] < array[right]) {
        max = right
      }

      if (max !== index) {
        _swap(array, max, index)
        index = max
      } else {
        break
      }
    }
  }

  const _buildMaxHeap = array => {
    let i, parent = Math.floor(array.length / 2) - 1

    for (i = parent; i >= 0; i--) {
      _maxHeap(array, i, array.length)
    }
  }

  const _sort = array => {
    _buildMaxHeap(array)

    for (let i = array.length - 1; i > 0; i--) {
      _swap(array, 0, i)
      _maxHeap(array, 0, i)
    }
    return array
  }

  return _sort(array)
}

```
