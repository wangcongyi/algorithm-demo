### 杨辉三角

```

杨辉三角，是二项式系数在三角形中的一种几何排列  
在欧洲，这个表叫做帕斯卡三角形
下面 demo 只是计算某行的值  整个三角形类似

```
![PascalTriangle](https://github.com/wangcongyi/learning-algorithm/blob/master/images/t.gif)


```js

const pascalTriangle = lineNumber => {
  const currentLine = [1]
  const currentLineSize = lineNumber + 1

  for (let numIndex = 1; numIndex < currentLineSize; numIndex += 1) {
    currentLine[numIndex] = currentLine[numIndex - 1] * (lineNumber - numIndex + 1) / numIndex
  }

  return currentLine
}

////// 递归方法 /////
const pascalTriangleRecursive = lineNumber => {
  if (lineNumber === 0) {
    return [1]
  }

  const currentLineSize = lineNumber + 1
  const previousLineSize = currentLineSize - 1
  const currentLine = []
  const previousLine = pascalTriangleRecursive(lineNumber - 1)

  for (let numIndex = 0; numIndex < currentLineSize; numIndex += 1) {
    const leftCoefficient = (numIndex - 1) >= 0 ? previousLine[numIndex - 1] : 0
    const rightCoefficient = numIndex < previousLineSize ? previousLine[numIndex] : 0
    currentLine[numIndex] = leftCoefficient + rightCoefficient
  }

  return currentLine
}
  
```
