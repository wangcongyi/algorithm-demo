##### calculus
#### ![image](https://github.com/wangcongyi/algorithm-demo/assets/13843979/8eea843a-97a4-477f-b124-621267f414f3)

```javascript

const derivative = (f, x, h = 1e-5) => {
    return (f(x + h) - f(x)) / h
  }

  // Example usage:
  // Define a function, for example, f(x) = x^2
  const square = (x) => {
    return x * x
  }

  // Calculate the derivative of f(x) = x^2 at x = 3
  const x = 3
  const derivativeAtX = derivative(square, x)

```

