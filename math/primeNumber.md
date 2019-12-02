### prime number

```
质数（prime number）又称素数，有无限个   
一个大于1的自然数，除了1和它本身外，不能被其他自然数整除  
换句话说就是该数除了1和它本身以外不再有其他的因数

```
![prime number](https://github.com/wangcongyi/learning-algorithm/blob/master/images/prime.jpg)

```js

const testPrime = (number) => {
  if (number % 1 !== 0) {
    return false
  }

  if (number <= 1) {
    return false
  }

  if (number <= 3) {
    return true
  }

  if (number % 2 === 0) {
    return false
  }

  const dividerLimit = Math.sqrt(number)

  for (let d = 3; d <= dividerLimit; d += 2) {
    if (number % d === 0) {
      return false
    }
  }

  return true
}

```
