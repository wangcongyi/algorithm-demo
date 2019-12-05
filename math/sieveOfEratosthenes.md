### 埃拉托色尼筛选法 

```
埃氏筛法(the Sieve of Eratosthenes)，是古希腊数学家埃拉托色尼提出的一种筛选法 
用于求一定范围内的素数  

（1）先把1删除（现今数学界1既不是质数也不是合数）
（2）读取队列中当前最小的数2，然后把2的倍数删去
（3）读取队列中当前最小的数3，然后把3的倍数删去
（4）读取队列中当前最小的数5，然后把5的倍数删去
（5）读取队列中当前最小的数7，然后把7的倍数删去
（6）如上所述直到需求的范围内所有的数均删除或读取

复杂度 O(n log(log n))

```
![埃氏筛法](https://github.com/wangcongyi/learning-algorithm/blob/master/images/a.gif)


```js

const sieveOfEratosthenes = (maxNumber) => {
  const isPrime = new Array(maxNumber + 1).fill(true)
  isPrime[0] = false
  isPrime[1] = false

  const primes = []

  for (let number = 2; number <= maxNumber; number += 1) {
    if (isPrime[number] === true) {
      primes.push(number)
      let nextNumber = number * number

      while (nextNumber <= maxNumber) {
        isPrime[nextNumber] = false
        nextNumber += number
      }
    }
  }

  return primes
}

```
