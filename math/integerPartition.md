### 整数分拆

```

一个正整数可以写成一些正整数的和  
在数论上 跟这些和式有关的问题称为整数拆分、整数剖分、整数分割、分割数或切割数(Integer partition)

比如  4 = 4
      4 = 3 + 1
      4 = 2 + 2
      4 = 2 + 1 + 1
      4 = 1 + 1 + 1 + 1
      可以用5种方式写成

```

```js

const integerPartition = number => {
  const partitionMatrix = Array(number + 1).fill(null).map(() => {
    return Array(number + 1).fill(null)
  })

  for (let a = 1; a <= number; a += 1) {
    partitionMatrix[0][a] = 0
  }

  for (let b = 0; b <= number; b += 1) {
    partitionMatrix[b][0] = 1
  }

  for (let x = 1; x <= number; x += 1) {
    for (let y = 1; y <= number; y += 1) {
      if (x > y) {
        partitionMatrix[x][y] = partitionMatrix[x - 1][y]
      } else {
        const a = partitionMatrix[x - 1][y]
        const b = partitionMatrix[x][y - x]
        partitionMatrix[x][y] = a + b
      }
    }
  }

  return partitionMatrix[number][number]
}

```
