### Fibonacci Number


```

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...
F(1) = 1
F(2) = 1
F(n) = F(n-1) + F(n-2)（n>=3，n∈N*）

斐波那契数列 这个数列从第3项开始，每一项都等于前两项之和

```

```js

const fibonacci = (n) => {
  const sequence = [1]
  let currentValue = 1
  let previousValue = 0

  if (n === 1) {
    return sequence
  }

  let iteration = n - 1

  while (iteration) {
    currentValue += previousValue
    previousValue = currentValue - previousValue

    sequence.push(currentValue)
    iteration -= 1
  }

  return sequence
}

```

