### 冒泡排序

```

它重复地走访过要排序的元素列，依次比较两个相邻的元素 
如果顺序（如从大到小、首字母从从Z到A）错误就把他们交换过来  
走访元素的工作是重复地进行直到没有相邻元素需要交换，也就是说该元素列已经排序完成

```

![冒泡排序](https://github.com/wangcongyi/learning-algorithm/blob/master/images/bubbleSort.gif)

```js

const bubbleSort = arr => {
  const len = arr.length
  let temp
  for (let i = 0; i < len; i++) {
    for (let j = 0; j < len - 1 - i; j++) {
      if (arr[j] > arr[j + 1]) {
        temp = arr[j + 1]
        arr[j + 1] = arr[j]
        arr[j] = temp
      }
    }
  }
  return arr
}

```
