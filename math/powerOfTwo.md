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
