### 判断一个数是否是 2 的几次幂


**常规方法：不断取模与除以 2**
```js

const isPowerOfTwo = number => {
    if (number < 1) {
      return false
    }

    let dividedNumber = number

    while (dividedNumber !== 1) {
      if (dividedNumber % 2 !== 0) {
        return false
      }

      dividedNumber = dividedNumber / 2
    }

    return true
  }

```

**位运算方法：**

```

1 的二进制为 0001  
2 的二进制为 0010  
4 的二进制为 0100
8 的二进制为 1000
...
...
...

```

```js

const isPowerOfTwo = (number) => {
    if (number < 1) {
      return false
    }
    
    return (number & (number - 1)) === 0
  }

```


### 快速计算数字的幂运算


```

一般计算数字的幂运算  a^b = a * a * a * ... * a (b 个 a) 
复杂度为 O(n)

但是 用 a^b 为例子 计算到一半的时候其实就不用了计算了

如果 b 为偶数 a^b = a^(b / 2) * a^(b / 2)        ----->>   2^4 = (2^2) * (2^2)
如果 b 为奇数 a^b = a^(b // 2) * a^(b // 2) * a  ----->>   2^7 = (2^3) * (2^3) * (2)
b // 2 表示 b 除以 2 得整数
按照这个思路 
复杂度为 O(log(n))

```

```js

const fastPowering = (base, power) => {
  if (power === 0) {
    return 1
  }

  if (power % 2 === 0) {
    const multiplier = fastPowering(base, power / 2)
    return multiplier * multiplier
  }

  const multiplier = fastPowering(base, Math.floor(power / 2))
  return multiplier * multiplier * base
}

```


### 判断数字有几位  不转移成字符串的形式

```js

const len = Math.ceil(Math.log10(num + 1))

```


