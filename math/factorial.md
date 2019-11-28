### 阶乘定义

```
n! = n * (n - 1) * (n - 2).... * 1  
```

 **一般示例代码**
 
```js

const factorial = (num) => {
  let res = 1

  for (let i = 2; i <= num; i += 1) {
    res *= i
  }

  return res
}

```

**尾递归示例代码**

```js

const factorialRecursive = (number) => {
  return number > 1 ? number * factorialRecursive(number - 1) : 1;
}


const factorialRecursive = (num, res = 1) => {
    return num === 1 ? res : factorialRecursive(num - 1, num * res)
  }

```

函数调用自身称为递归 如果尾调用自身就称为尾递归  
递归非常耗费内存 很容易发生栈溢出错误 （Stack Overflow）  
所以一般尾递归优化的思维是 把内部变量变成参数的形式
