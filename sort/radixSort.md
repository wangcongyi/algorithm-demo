#### 基数排序

```

基数排序是按照低位先排序，然后收集；再按照高位排序，然后再收集；依次类推，直到最高位
有时候有些属性是有优先级顺序的，先按低优先级排序，再按高优先级排序
最后的次序就是高优先级高的在前，高优先级相同的低优先级高的在前
基数排序基于分别排序，分别收集，所以是稳定的
但基数排序的性能比桶排序要略差，每一次关键字的桶分配都需要 O(n) 的时间复杂度
而且分配之后得到新的关键字序列又需要 O(n) 的时间复杂度
假如待排数据可以分为 d 个关键字，则基数排序的时间复杂度将是 O(d*2n) 
当然 d 要远远小于 n ，因此基本上还是线性级别的
基数排序的空间复杂度为 O(n+k) ，其中k为桶的数量。一般来说 n>>k ，因此额外空间需要大概 n 个左右

```

![基数排序](https://github.com/wangcongyi/learning-algorithm/blob/master/images/radixSort.webp)

```js

const radixSort = (arr, n, radix = 10) => {
  if (!n) {
    n = arr[0].toString().length
  }
  let i, j, tmp, num, queues = [], q = arr.slice()
  for (i = 0; i < radix; i++) {
    queues.push([])
  }
  for (i = 0; i < n; i++) {
    while (q.length > 0) {
      tmp = q.shift()
      num = Math.floor(tmp / Math.pow(radix, i) % radix)
      queues[num].push(tmp)
    }
    for (j = 0; j < radix; j++) {
      while (queues[j].length > 0) {
        q.push(queues[j].shift())
      }
    }
  }
  return q
}

```
