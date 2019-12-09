### 洗牌算法

```

Fisher–Yates 随机置乱算法也被称做高纳德置乱算法,通俗说就是生成一个有限集合的随机排列

```

```js

const fisherYates = (originalArray) => {
  const array = originalArray.slice(0)

  for (let i = (array.length - 1); i > 0; i -= 1) {
    const randomIndex = Math.floor(Math.random() * (i + 1));
    [array[i], array[randomIndex]] = [array[randomIndex], array[i]]
  }

  return array
}

```
