#### 桶排序

```

桶排序是计数排序的升级版 它利用了函数的映射关系，高效与否的关键就在于这个映射函数的确定
假设输入数据服从均匀分布，将数据分到有限数量的桶里，每个桶再分别排序 有可能再使用别的排序算法或是以递归方式继续使用桶排序进行排
桶排序最好情况下使用线性时间 O(n) 
桶排序的时间复杂度，取决与对各个桶之间数据进行排序的时间复杂度，因为其它部分的时间复杂度都为 O(n)
很显然，桶划分的越小，各个桶之间的数据越少，排序所用的时间也会越少。但相应的空间消耗就会增大

```

```js

const bucketSort = (arr, bucketSize = 5) => {
  if (arr.length === 0) {
    return arr
  }

  let minValue = arr[0]
  let maxValue = arr[0]
  for (let i = 1; i < arr.length; i++) {
    if (arr[i] < minValue) {
      minValue = arr[i]
    } else if (arr[i] > maxValue) {
      maxValue = arr[i]
    }
  }

  const bucketCount = Math.floor((maxValue - minValue) / bucketSize) + 1
  const buckets = new Array(bucketCount)
  for (let i = 0; i < buckets.length; i++) {
    buckets[i] = []
  }

  for (let i = 0; i < arr.length; i++) {
    buckets[Math.floor((arr[i] - minValue) / bucketSize)].push(arr[i])
  }

  arr.length = 0
  for (let i = 0; i < buckets.length; i++) {
    insertionSort(buckets[i])
    for (let j = 0; j < buckets[i].length; j++) {
      arr.push(buckets[i][j])
    }
  }
  return arr
}

```
