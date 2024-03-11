#### The normal distribution
#### ![image](https://github.com/wangcongyi/algorithm-demo/assets/13843979/9481e9fa-813e-4b71-8f81-63b3975d611a)

```javascript

 const normalDistributionPDF = (x, mu, sigma) => {
    const sqrtTwoPi = Math.sqrt(2 * Math.PI)
    const exponent = -0.5 * ((x - mu) / sigma) ** 2
    return (1 / (sigma * sqrtTwoPi)) * Math.exp(exponent)
  }

  // Example usage:
  const mu = 0 // Mean
  const sigma = 1 // Standard deviation (for a standard normal distribution)
  const x = 1 // Value to evaluate the PDF at
  const value = normalDistributionPDF(x, mu, sigma)

```
